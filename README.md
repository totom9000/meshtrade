# MeshPool Trade

Trade coins with other miners, wallet to wallet, without an exchange.

MeshPool Trade is a desktop app for Windows and Linux. It holds your own
wallet on your own computer and settles every trade as an **atomic swap**:
both sides lock their coins in a contract on their own chain, and either
both contracts pay out or both refund. Nobody, MeshPool included, ever holds
your coins.

The order book is live at **[meshpool.net/trade](https://meshpool.net/trade)**.
The Buy and Sell buttons there open the order in the app, and nothing
happens until you confirm it in the app's own window.

## Download

Get the latest version from **[Releases](https://github.com/totom9000/meshtrade/releases/latest)**.

| System | File |
|---|---|
| Windows 10/11, 64-bit | `meshpool-trade-win-<version>.zip` |
| Linux, x86-64 | `meshpool-trade-linux-<version>.tar.gz` |

Each release lists the SHA-256 checksum of every file in `SHA256SUMS.txt`.
Check it before you run anything:

```bash
sha256sum -c SHA256SUMS.txt
```

On Windows, in PowerShell:

```powershell
Get-FileHash .\meshpool-trade-win-0.4.2.zip -Algorithm SHA256
```

## Getting started

**Windows.** Unzip, then double-click `meshpool-trade.exe`.

**Linux.**

```bash
tar xzf meshpool-trade-linux-0.4.2.tar.gz
cd meshpool-trade-linux
./meshpool-trade
```

On first start you choose the network (`main` for real coins) and create a
wallet. **Write the 24 recovery words down on paper.** They are shown once,
and they are the only way back to your coins if the computer dies. After
that the app opens with your password, or with Windows Hello or your
system keyring if you turn that on under Settings → Security.

Fund the wallet by sending coins to the addresses on the Wallet screen. You
can also point your MeshPool payout address at it, so mined coins land
where you can trade them.

## Trading

- **Take an offer.** Pick a pair, enter how much you want, and the app fills
  it from the best offers up to your price limit. You see the breakdown and
  the fee before you confirm.
- **Place an offer.** Set your price and amount. Your coins stay in your
  wallet until someone takes the offer. Keep the app running so it can
  complete the trade.
- **Bots.** A grid bot, an accumulation bot that buys dips, and a DCA bot
  that buys on a schedule. They run inside the app on your computer, with
  your own coins.

A swap takes as long as the two chains need for a few confirmations each,
usually 10 to 40 minutes. If the other side disappears, your coins come back
on their own when the contract's time lock opens. If you close the app, it
picks up where it left off when you start it again.

## Supported coins

Lumenite (LMT), Riecoin (RIC), RCPU, ConnectCoin (CONN), Avian (AVN),
Bitcoin (BTC), Litecoin (LTC), and USDC on Polygon.

Which pairs are open right now is shown on
[meshpool.net/trade](https://meshpool.net/trade). USDC swaps have an early
limit per trade, shown in the app and on the Trade page. To trade USDC you
also need a little POL in the same wallet to pay Polygon's network fee.

## Fees

Each side pays **0.2 %** of what it gives, in its own coin, before the swap
starts. The other side's app checks the payment on chain. The app shows the
fee before every trade, and the fee is not refunded if a swap fails. The
chains' own network fees come on top. There are no deposit, withdrawal or
listing fees.

## Running on a rig without a screen

The same program works from the command line:

```bash
./meshpool-trade init --net main
./meshpool-trade wallet create
./meshpool-trade serve
./meshpool-trade --help
```

On Windows, add `| Out-Host` to the end of a command in PowerShell, so the
shell waits for the output. The README inside the download has the full list
of commands.

## Safety

- Your keys never leave your computer. MeshPool never sees them.
- A link from the website never trades by itself. The app always asks.
- Keep your 24 words offline. Anyone who has them owns your coins.
- MeshPool will never ask for your recovery words or your password.

## Licence

Proprietary. Copyright © 2026 MeshPool, all rights reserved. The program is
provided as binaries only, under the licence in `LICENSE.txt` inside each
download. Third-party components are listed with their licences in
`THIRD-PARTY-LICENSES.txt`.
