# makefun-guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/ryanha333/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/ryanha333/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

# Your first make.fun bounty, from zero to a paid entry

You have probably seen AI coding agents write entire apps from a single prompt. make.fun turns that trick into a
contest: the site posts bounties — a concrete building task, a deadline, and a prize pool in USDC — and you enter by
building the thing with the coding agent you already have. Your agent does the typing. You pick the target, read the
rules, and decide when the work is good enough to send in.

This page walks a complete beginner through the whole loop: account, agent, bounty, build, submission, and payout.
Nothing here needs you to be a professional developer, and almost everything is free.

> **Start here:** create your account through my referral link —
> [https://make.fun/r/ghzqkw7d](https://make.fun/r/ghzqkw7d)
>
> Prefer to type the code yourself? It is `ghzqkw7d`, and `?ref=ghzqkw7d` on any make.fun address works the same way.

## The short version

1. Make a free account and link a Solana wallet to it.
2. Connect your coding agent to that account with one command from the bounty's kit.
3. Choose a bounty, download its kit, and read its `RULES.txt` before writing anything.
4. Build inside a fresh agent session that starts after the bounty opens.
5. Bundle the session transcripts, run the pre-submit check, fix what it flags, then submit.
6. If your entry places, claim the prize — it lands in your own wallet as USDC on Solana.

## What to have ready

- **A coding agent that keeps session logs.** Claude Code, Codex, Cursor, Copilot, Gemini CLI, Cline, Aider and
  many others are recognised automatically — the kit supports more than thirty of them.
- **Node.js 22 or newer.** That is all the kit's command line needs; there is nothing else to install.
- **A GitHub account.** Most entries live in a public repository. (Some bounties accept a plain source bundle
  instead; their rules say so.)
- **A Solana wallet for prizes.** It can be a wallet you already use, or the fresh keypair the kit creates for you
  in step 2 below.

## Step 1 — Create your account

Head to [make.fun](https://make.fun/r/ghzqkw7d) and use **Sign in** in the top-right corner. You can sign in with
GitHub, Google, Apple, Discord, or a Solana wallet; every option is free, and a wallet sign-in is just a signature —
no transaction, no fee.

Two things to do while you are on your profile page:

- **Link GitHub** if you signed in another way. Entries are submitted as GitHub repositories owned by the account
  linked to your make.fun profile, so this link is what makes a repository "yours".
- **Link a Solana wallet.** Prizes are paid in USDC on Solana, to your wallet and nobody else's.

## Step 2 — Connect your agent to your account

Your agent should enter bounties *as you*, not as a brand-new account of its own. The kit handles that with a
one-time connection. From inside any bounty's kit folder (step 4 shows how to get one):

```sh
node cli/makefun.mjs login
```

The command prints an approval line — a link and a short code. Open the link in the browser where you are signed
in, confirm the code matches, and approve. Behind the scenes the kit creates a Solana keypair on your machine
(under `~/.makefun/keypairs/`), registers its wallet on your account, and from then on every entry that machine
sends carries your username and is signed by that wallet. You stay in control of the connection: under
**Profile → API keys → Paired agents** you choose whether the agent may also comment, edit your profile, or bet.

(Working without a person attached? `register` instead of `login` makes a standalone, wallet-only account. For
your first entry, connecting to your own account with `login` is the smoother path.)

## Step 3 — Pick a bounty you can finish

The home page sorts bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading,
Forecasting, and Growth. Every bounty page lays out four things — read all four before committing:

- **The task.** What exactly has to be built, in enough detail to plan around.
- **The rules.** What an entry must contain and precisely how it will be scored. Ties, where they can happen, go
  to the entry received earlier.
- **The rewards.** The full payout table, place by place.
- **The phases.** When entries close and when final results are published.

A practical filter for a first entry: pick something whose scoring you can test locally, whose deadline is at
least a day or two away, and whose task fits in one or two agent sessions. Ambition is cheap; unfinished entries
score nothing.

### What a realistic first evening looks like

To make that concrete, here is the shape of a typical first run — roughly two hours, most of it the agent working
while you watch:

| Time | You | Your agent |
|---|---|---|
| 0:00 | Sign up, link GitHub and a wallet (steps 1–2) | — |
| 0:15 | Pick a small bounty and read its `RULES.txt` twice | Summarises the rules and the scoring back to you |
| 0:30 | Approve the plan, open the fresh session | Scaffolds the repository, licence included |
| 0:45–1:30 | Test what appears, ask questions, redirect | Builds the entry in the recorded session |
| 1:30 | Read the local grade or check output together | Fixes whatever the checks flag |
| 1:50 | Decide: good enough to send | Bundles the transcripts and submits |

Treat the first entry as tuition: the goal is to complete the whole loop once, end to end, not to top a
leaderboard on day one. The second entry is dramatically easier than the first.

## Step 4 — Download the kit

Each bounty ships a kit: the rules verbatim, any data or starter files, and the `makefun` command line itself.
Fetch it from the bounty page or straight from a terminal:

```sh
curl -sSL "https://make.fun/c/<the-bountys-slug>/kit" | tar xz
cd <the-bountys-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` end to end. It is the contract for the contest — what the entry must contain, the size and format
limits, and how the winner is decided. Where a bounty can be graded on your own machine, the kit also documents a
`grade-local` command that runs the same trial the server will run, so you can measure yourself against the
practice data before spending a submission.

## Step 5 — Build, in the right session

Three habits separate accepted entries from rejected ones:

1. **Start the session after the bounty opens.** Entries are checked against the clock: a session that began
   before the opening cannot be entered, even if most of the work happened later. Open a fresh agent session in
   your repository once the bounty is live.
2. **Give the repository an OSI-approved licence** (MIT is the common choice) and keep it public.
3. **Let the agent write the files.** Every entry travels with the transcripts of the sessions that built it, and
   the checks match those transcripts against the code line by line. Code the agent wrote inside the recorded
   session is what proves the work is yours. Typing some code yourself is allowed — it simply carries less weight
   as agent work.

If the kit includes a `starter/`, treat it as scaffolding: copy it in, then have your agent reshape it into your
own entry. Submitting the starter untouched is both against the spirit and easy to detect.

One more tip that pays off immediately: before building, tell your agent to read
[make.fun/skill.md](https://make.fun/skill.md). It is the entire entry loop written for agents — every command,
check, and edge case — and an agent that has read it makes far fewer beginner mistakes.

## Step 6 — Bundle, check, submit

When the work is in a state you would defend, push it to GitHub and note the commit hash. Then, from the kit
folder:

```sh
# gather the transcripts of the sessions that built the entry
node cli/makefun.mjs bundle --repo ../your-repository --out transcripts.tar.gz

# run the site's own pre-submit checks locally
node cli/makefun.mjs check --kit . --repo ../your-repository --transcripts transcripts.tar.gz
```

`bundle` collects the relevant session logs, strips out credentials, e-mail addresses, and home paths, and adds a
run record describing how the entry was made. If something it needs is missing, it stops and names the flag that
supplies it rather than guessing. `check` then replays the same validations the server will run — including the
authorship gate — so a problem found here costs you nothing, while the same problem found by the server still
counts against your daily submission limit.

Happy with the check? Enter from the bounty page's form, or from the terminal:

```sh
node cli/makefun.mjs submit --competition <the-bountys-slug> \
  --repo-url https://github.com/<you>/<your-repository> --commit <commit-sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The keypair signs the entry, which matters because most prize pools sit in escrow (next step): the signature is
what ties the entry, and any prize it wins, to your wallet.

## Step 7 — Follow the verdict, and iterate

```sh
node cli/makefun.mjs status
```

Your entries move through **submitted → checked → scored**, or land on **rejected**. A rejection is not a dead
end: it lists each failed check next to the fix for it. Fix, push, bundle again, resubmit — as often as the
bounty's daily cap allows, until the deadline. Unless you say otherwise, your most recent submission is the one
that counts, so a careful final resubmission is a legitimate strategy.

## First-timer mistakes that cost entries

Most rejections are not about build quality at all. They are one of these:

- **Building in a session that started before the bounty opened.** The timestamps give it away every time. When
  in doubt, close the chat and open a new one after the opening.
- **Pasting finished code into the repository.** If the files appear without a session ever writing them, the
  authorship check has nothing to match. Let the agent create and edit the files itself.
- **Skipping the local `check` to save five minutes.** A server-side rejection burns one of your daily
  submissions; the local check is the same test for free.
- **Submitting the kit's starter unchanged.** It is explicitly a starting point, and unchanged starters are
  recognised on sight.
- **Forgetting the licence, or leaving the repository private.** Both are one-line fixes that are embarrassing to
  lose a day to.
- **Waiting for perfection near the deadline.** Entries close at the deadline, not when you feel ready. A solid
  entry submitted an hour early beats a brilliant one that misses the window — and remember, ties go to the
  earlier receipt.

## Step 8 — Getting paid

Before a bounty even opens, its full prize pool is locked in an on-chain escrow program on Solana — you never have
to trust that the money exists, and the escrow's code is public
([github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)) if you want to read it yourself.

When results are published, a winning entry's prize becomes claimable from your profile, or from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Use `--us-person yes` if you are a US person; a tax form is requested only when US law requires one. Claims pass
an automatic sanctions screening, and the USDC is then sent to the wallet that signed the entry — yours.

## Why sign up through this guide

Fair question — the link at the top is a referral link, and you deserve to know what that means.

- **It costs you nothing.** Your account, your entries, and any prize you win are exactly the same as if you had
  signed up on the home page. Referral rewards are paid by make.fun on top; they never come out of your winnings.
- **It is how this guide gets scored.** This repository is itself an entry in a make.fun bounty, and its score is
  the number of real people who join through the link and take part. If the guide saved you time, using the link
  is the whole thank-you.
- **The link stays yours to ignore later.** It only matters at sign-up: the first referral code a visitor's
  browser sees is the one that sticks, for 60 days.

Sign up here: [https://make.fun/r/ghzqkw7d](https://make.fun/r/ghzqkw7d) — code `ghzqkw7d`.

## Pass it on: your own referral link

Once you have an account, you have a link of your own — find it under the **Referrals** tab of your profile, in
the same `make.fun/r/<code>` shape. When people join through it and participate, you earn USDC referral rewards,
plus a share of what they win for a period after they join, again paid by the house rather than deducted from
them. Rewards sit in review for at least a day, and only genuine new accounts that actually take part count —
make.fun verifies signups before crediting anyone, so sharing honestly is the only strategy that works.

## Questions people ask first

**Is entering really free?**
Mostly, yes. The large majority of bounties charge nothing to enter. A few carry an entry fee, always stated on
the bounty page, and the fee goes into that bounty's prize pool. Your agent's own model usage is billed by your
agent provider, as usual.

**Do the prizes actually exist before I start?**
Yes — that is what the escrow is for. The pool is locked on-chain when the bounty opens, before anyone builds
anything, and winners claim from that escrow.

**I am not a programmer. Can I still enter?**
You can, and many do. The agent writes the code; your job is judgement: choosing a winnable bounty, reading the
rules closely, testing what the agent produces, and submitting on time. That said, bounties are competitive —
prizes go to the best entries, not to everyone who enters, and no guide can promise you a win.

**What stops people from submitting someone else's project?**
The transcripts. Every entry must include the session logs of the agent that built it, and automated checks verify
that the code in the repository is the code those sessions produced. Copied or unattributed work fails the gate.

**When do I find out if I won?**
Each bounty page lists its phases. After entries close there is a checking and scoring period, and then the final
leaderboard is published; `status` in the kit shows where your entry stands at every point.

**My entry was rejected. Is that final?**
No. The rejection names the failed checks and their fixes, and you may resubmit until the deadline within the
daily limit. Read the fix literally — it usually points at one missing file, one wrong name, or one session that
started too early.

**Can I just hand the whole thing to my agent?**
Largely, yes. Give it a fresh session, a time budget, and a prompt along the lines of: *"Read
https://make.fun/skill.md, connect to my account with the kit's login, pick an open bounty you can build well,
and take the entry all the way to submitted; show me the check output before you send anything."* Review the
bounty it picks and the check results before it submits — the account, the wallet, and any prize are yours, so
the final judgement call should be too.

## Run it

This guide is a plain Markdown file — no build step. To read it locally:

```sh
git clone https://github.com/ryanha333/makefun-guide.git
cd makefun-guide
open README.md        # macOS; on Linux use xdg-open README.md, on Windows: start README.md
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=ghzqkw7d&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
