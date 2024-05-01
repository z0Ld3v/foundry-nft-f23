# Mood NFT
The Mood NFT is a unique ERC721 token that allows owners to express their current mood through their NFT. The contract is written in Solidity and can be used with Hardhat and Foundry for development and testing.

## Features

- Owners can mint a new Mood NFT
- Each Mood NFT can be in one of two states: Happy or Sad
- Only the owner of the NFT can flip the mood of their token
- The token URI (metadata) is dynamically generated based on the current mood of the NFT
## How it works

The Mood NFT contract extends the OpenZeppelin `ERC721` implementation, providing standard NFT functionality. It also utilizes the `Base64` library from OpenZeppelin for encoding the token URI.

The contract maintains a `s_tokenIdToMood` mapping that associates each token ID with its current mood (Happy or Sad). When a new NFT is minted, it is initially set to the Happy mood.

The `flipMood` function allows the owner of an NFT to change the mood of their token from Happy to Sad, or vice versa. This function includes a check to ensure that only the approved or owner of the NFT can modify its mood.

The `tokenURI` function is overridden to dynamically generate the metadata for each NFT based on its current mood. The metadata includes the name, description, attributes, and image of the NFT. The image URI is determined by the current mood of the NFT, with separate SVG image URIs for Happy and Sad moods.

## Usage with Hardhat
To use the Mood NFT contract with Hardhat, follow these steps:

1. Install the necessary dependencies:
```zsh
npm install --save-dev @nomiclabs/hardhat-ethers @openzeppelin/contracts
```


2. Import the contract in your Hardhat script or test file:
```js
const MoodNft = await ethers.getContractFactory("MoodNft");
```


3. Deploy the contract with the desired SVG image URIs:
```js
const happySvgImageUri = "..."; // Replace with your happy SVG image URI
const sadSvgImageUri = "..."; // Replace with your sad SVG image URI
const moodNft = await MoodNft.deploy(sadSvgImageUri, happySvgImageUri);
```


4. Interact with the contract using the deployed instance:
```js
await moodNft.mintNft(); // Mint a new Mood NFT
await moodNft.flipMood(tokenId); // Flip the mood of an NFT
const tokenUri = await moodNft.tokenURI(tokenId); // Get the token URI of an NFT
```


## Usage with Foundry
To use the Mood NFT contract with Foundry, follow these steps:

1. Install the necessary dependencies:
```zsh
forge install OpenZeppelin/openzeppelin-contracts
```


2. Import the contract in your Foundry test file:
```solidity
import {MoodNft} from "src/MoodNft.sol";
```


3. Deploy the contract with the desired SVG image URIs in your test:
```solidity
string memory happySvgImageUri = "..."; // Replace with your happy SVG image URI
string memory sadSvgImageUri = "..."; // Replace with your sad SVG image URI
MoodNft moodNft = new MoodNft(sadSvgImageUri, happySvgImageUri);
```


4. Interact with the contract using the deployed instance:
```solidity
moodNft.mintNft(); // Mint a new Mood NFT
moodNft.flipMood(tokenId); // Flip the mood of an NFT
string memory tokenUri = moodNft.tokenURI(tokenId); // Get the token URI of an NFT
```


Feel free to explore and extend the functionality of the Mood NFT contract to suit your specific requirements. Happy coding!



# foundry-nft-f23
