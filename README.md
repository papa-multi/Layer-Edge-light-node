# Clone the Repository & Navigate to the Directory

```
git clone https://github.com/Layer-Edge/light-node.git
cd light-node
```
# Install Go (Version 1.18 or higher)

```
curl -OL https://go.dev/dl/go1.22.0.linux-amd64.tar.gz
rm -rf /usr/local/go
tar -C /usr/local -xzf go1.22.0.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
go version  # Check installation
```

#  Install Rust (Version 1.81 or higher)

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustc --version  # Check installation
```

# Install Risc0 Toolchain

```
source "/root/.bashrc"
```

```
curl -L https://risczero.com/install | bash && rzup install
```

# Configure Environment Variables

```
nano .env
```

save them in a ```.env file``` with out 0x

```
export GRPC_URL=34.31.74.109:9090
export CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
export ZK_PROVER_URL=http://127.0.0.1:3001
export API_REQUEST_TIMEOUT=100
export POINTS_API=http://127.0.0.1:8080
export PRIVATE_KEY='cli-node-private-key'
```

# Start the Merkle Service

```
screen -S risc0-merkle-service
```
```
cd risc0-merkle-service
cargo build && cargo run
```
ctrl+A+D

# Build & Run the Light Node
```
screen -S CLI
```
```
cd ~/light-node
go build
./light-node
```
# Check your earned points via CLI

(Replace {walletAddress} with your actual CLI wallet address.)

```
curl https://light-node.layeredge.io/api/cli-node/points/{walletAddress}
```
