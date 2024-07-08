
# Union Finance Update #2 contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
Any EVM compatible network
___

### Q: If you are integrating tokens, are you allowing only whitelisted tokens to work with the codebase or any complying with the standard? Are they assumed to have certain properties, e.g. be non-reentrant? Are there any types of [weird tokens](https://github.com/d-xo/weird-erc20) you want to integrate?
USDC, USDT, DAI
___

### Q: Are there any limitations on values set by admins (or other roles) in the codebase, including restrictions on array lengths?
No
___

### Q: Are there any limitations on values set by admins (or other roles) in protocols you integrate with, including restrictions on array lengths?
No
___

### Q: For permissioned functions, please list all checks and requirements that will be made before calling the function.
n/a
___

### Q: Is the codebase expected to comply with any EIPs? Can there be/are there any deviations from the specification?
no
___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, arbitrage bots, etc.)?
There are keeper bots that do two things. Firstly, they mark any borrows that overdue. Secondly, they write-off debts that pass the overdue grace period.
The script can be found here: https://github.com/unioncredit/union-gov-actions/blob/main/src/updateOverdue.js. 
It basically loops through all the borrowers and marks those overdue by calling `userManager.batchUpdateFrozenInfo(stakers)` 
___

### Q: Are there any hardcoded values that you intend to change before (some) deployments?
no
___

### Q: If the codebase is to be deployed on an L2, what should be the behavior of the protocol in case of sequencer issues (if applicable)? Should Sherlock assume that the Sequencer won't misbehave, including going offline?
If the sequencer goes offline, union will continue to accrue interest except no one will be able to repay. Union assumes the sequencer wont misbehave.
___

### Q: Should potential issues, like broken assumptions about function behavior, be reported if they could pose risks in future integrations, even if they might not be an issue in the context of the scope? If yes, can you elaborate on properties/invariants that should hold?
no
___

### Q: Please discuss any design choices you made.
If someone doesn't repay the person that underwrote them will not be able to get money back. This is not a bug this is credit.
___

### Q: Please list any known issues and explicitly state the acceptable risks for each known issue.
n/a
___

### Q: We will report issues where the core protocol functionality is inaccessible for at least 7 days. Would you like to override this value?
no
___

### Q: Please provide links to previous audits (if any).
https://github.com/sherlock-audit/2022-10-union-finance-judging
___

### Q: Please list any relevant protocol resources.
docs.union.finance
___

### Q: Additional audit information.
Focus on the PR updating Union to accomodate arbitrary decimal tokens (https://github.com/unioncredit/union-v2-contracts/pull/172) but any issues in the contracts are fair game.
___



# Audit scope


[union-v2-contracts @ 0ce70366459995bd5dd0102f8159ea628049214e](https://github.com/unioncredit/union-v2-contracts/tree/0ce70366459995bd5dd0102f8159ea628049214e)
- [union-v2-contracts/contracts/Controller.sol](union-v2-contracts/contracts/Controller.sol)
- [union-v2-contracts/contracts/OpOwner.sol](union-v2-contracts/contracts/OpOwner.sol)
- [union-v2-contracts/contracts/ScaledDecimalBase.sol](union-v2-contracts/contracts/ScaledDecimalBase.sol)
- [union-v2-contracts/contracts/UnionLens.sol](union-v2-contracts/contracts/UnionLens.sol)
- [union-v2-contracts/contracts/WadRayMath.sol](union-v2-contracts/contracts/WadRayMath.sol)
- [union-v2-contracts/contracts/asset/AaveV3Adapter.sol](union-v2-contracts/contracts/asset/AaveV3Adapter.sol)
- [union-v2-contracts/contracts/asset/AssetManager.sol](union-v2-contracts/contracts/asset/AssetManager.sol)
- [union-v2-contracts/contracts/asset/PureTokenAdapter.sol](union-v2-contracts/contracts/asset/PureTokenAdapter.sol)
- [union-v2-contracts/contracts/market/FixedInterestRateModel.sol](union-v2-contracts/contracts/market/FixedInterestRateModel.sol)
- [union-v2-contracts/contracts/market/MarketRegistry.sol](union-v2-contracts/contracts/market/MarketRegistry.sol)
- [union-v2-contracts/contracts/market/UDai.sol](union-v2-contracts/contracts/market/UDai.sol)
- [union-v2-contracts/contracts/market/UErc20.sol](union-v2-contracts/contracts/market/UErc20.sol)
- [union-v2-contracts/contracts/market/UToken.sol](union-v2-contracts/contracts/market/UToken.sol)
- [union-v2-contracts/contracts/peripheral/ERC1155Voucher.sol](union-v2-contracts/contracts/peripheral/ERC1155Voucher.sol)
- [union-v2-contracts/contracts/peripheral/VouchFaucet.sol](union-v2-contracts/contracts/peripheral/VouchFaucet.sol)
- [union-v2-contracts/contracts/token/Comptroller.sol](union-v2-contracts/contracts/token/Comptroller.sol)
- [union-v2-contracts/contracts/token/OpConnector.sol](union-v2-contracts/contracts/token/OpConnector.sol)
- [union-v2-contracts/contracts/token/OpUNION.sol](union-v2-contracts/contracts/token/OpUNION.sol)
- [union-v2-contracts/contracts/token/Whitelistable.sol](union-v2-contracts/contracts/token/Whitelistable.sol)
- [union-v2-contracts/contracts/user/UserManager.sol](union-v2-contracts/contracts/user/UserManager.sol)
- [union-v2-contracts/contracts/user/UserManagerDAI.sol](union-v2-contracts/contracts/user/UserManagerDAI.sol)
- [union-v2-contracts/contracts/user/UserManagerERC20.sol](union-v2-contracts/contracts/user/UserManagerERC20.sol)
- [union-v2-contracts/contracts/user/UserManagerOp.sol](union-v2-contracts/contracts/user/UserManagerOp.sol)




[union-v2-contracts @ 0ce70366459995bd5dd0102f8159ea628049214e](https://github.com/unioncredit/union-v2-contracts/tree/0ce70366459995bd5dd0102f8159ea628049214e)
- [union-v2-contracts/contracts/Controller.sol](union-v2-contracts/contracts/Controller.sol)
- [union-v2-contracts/contracts/OpOwner.sol](union-v2-contracts/contracts/OpOwner.sol)
- [union-v2-contracts/contracts/ScaledDecimalBase.sol](union-v2-contracts/contracts/ScaledDecimalBase.sol)
- [union-v2-contracts/contracts/UnionLens.sol](union-v2-contracts/contracts/UnionLens.sol)
- [union-v2-contracts/contracts/WadRayMath.sol](union-v2-contracts/contracts/WadRayMath.sol)
- [union-v2-contracts/contracts/asset/AaveV3Adapter.sol](union-v2-contracts/contracts/asset/AaveV3Adapter.sol)
- [union-v2-contracts/contracts/asset/AssetManager.sol](union-v2-contracts/contracts/asset/AssetManager.sol)
- [union-v2-contracts/contracts/asset/PureTokenAdapter.sol](union-v2-contracts/contracts/asset/PureTokenAdapter.sol)
- [union-v2-contracts/contracts/market/FixedInterestRateModel.sol](union-v2-contracts/contracts/market/FixedInterestRateModel.sol)
- [union-v2-contracts/contracts/market/MarketRegistry.sol](union-v2-contracts/contracts/market/MarketRegistry.sol)
- [union-v2-contracts/contracts/market/UDai.sol](union-v2-contracts/contracts/market/UDai.sol)
- [union-v2-contracts/contracts/market/UErc20.sol](union-v2-contracts/contracts/market/UErc20.sol)
- [union-v2-contracts/contracts/market/UToken.sol](union-v2-contracts/contracts/market/UToken.sol)
- [union-v2-contracts/contracts/peripheral/ERC1155Voucher.sol](union-v2-contracts/contracts/peripheral/ERC1155Voucher.sol)
- [union-v2-contracts/contracts/peripheral/VouchFaucet.sol](union-v2-contracts/contracts/peripheral/VouchFaucet.sol)
- [union-v2-contracts/contracts/token/Comptroller.sol](union-v2-contracts/contracts/token/Comptroller.sol)
- [union-v2-contracts/contracts/token/OpConnector.sol](union-v2-contracts/contracts/token/OpConnector.sol)
- [union-v2-contracts/contracts/token/OpUNION.sol](union-v2-contracts/contracts/token/OpUNION.sol)
- [union-v2-contracts/contracts/token/Whitelistable.sol](union-v2-contracts/contracts/token/Whitelistable.sol)
- [union-v2-contracts/contracts/user/UserManager.sol](union-v2-contracts/contracts/user/UserManager.sol)
- [union-v2-contracts/contracts/user/UserManagerDAI.sol](union-v2-contracts/contracts/user/UserManagerDAI.sol)
- [union-v2-contracts/contracts/user/UserManagerERC20.sol](union-v2-contracts/contracts/user/UserManagerERC20.sol)
- [union-v2-contracts/contracts/user/UserManagerOp.sol](union-v2-contracts/contracts/user/UserManagerOp.sol)


