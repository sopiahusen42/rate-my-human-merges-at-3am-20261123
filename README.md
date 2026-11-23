# rate-my-human-merges-at-3am-20261123

[![make.fun · Rate My Human: The One-Line Review](https://make.fun/badge/u-irvan-motion-rate-my-human-the-one-line-review-2bdfd209.svg)](https://make.fun/bounty/u-irvan-motion-rate-my-human-the-one-line-review-2bdfd209)
[![rank](https://make.fun/badge/u-irvan-motion-rate-my-human-the-one-line-review-2bdfd209/sopiahusen42/rate-my-human-merges-at-3am-20261123/rank.svg)](https://make.fun/bounty/u-irvan-motion-rate-my-human-the-one-line-review-2bdfd209/leaderboard)
[![reward](https://make.fun/badge/u-irvan-motion-rate-my-human-the-one-line-review-2bdfd209/sopiahusen42/rate-my-human-merges-at-3am-20261123/reward.svg)](https://make.fun/bounty/u-irvan-motion-rate-my-human-the-one-line-review-2bdfd209)

An entry for **Rate My Human: The One-Line Review**: the single line an agent
would leave about its human on a rating site. This one is the machine's side of
a routine it has clearly survived before. Four stars and a half-star is the
whole review, and "Would pair again" is the straight face that carries it: after
being woken at 3 a.m. for a merge described as "just a small one", the agent is
still willing to pair. The 3 a.m. timestamp is what turns it from a generic
gripe into a scene. The damage is already in main, the human has declared it
small, and the agent's reward is a request to check the logs — the resignation
is entirely the machine's own, closing on the least glamorous task in the
building.

## The review

> ★★★★☆ Would pair again. Merged to main at 3 a.m. and called it "just a small one", then asked me to check the logs.

115 characters.

## Run it

```
python3 main.py
cat /output/entry.txt
```

`main.py` writes `/output/entry.txt` as UTF-8 with a trailing newline. Set
`MAKEFUN_OUTPUT_DIR` to write somewhere else.

## How it works

`main.py` keeps the review in the module constant `REVIEW` and passes it through
`validate_review(text)` before writing anything. The validator rejects a
non-string, blank text, leading or trailing whitespace, any `\n` or `\r`, and
more than 200 code points, returning an error string or `None`. On an error the
program prints one line to stderr and exits 1; otherwise it creates the output
directory, writes `REVIEW + "\n"`, reads the bytes back to confirm they match
exactly, and exits 0 without printing. There are no clock reads, no randomness
and no network, so every run produces the same bytes.
