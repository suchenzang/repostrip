# Demo of Commit Rewriting to Santize internal files

This repo is a demo of how you can easily use history rewriting to keep 2 repos in sync.

You have a leader which is where development takes place. This repo is read/write.

Additionally you have a follower repo. This repo has files/folders stripped out of it (and its entire history, it's as if they were never there). This repo is read only.

When new changes are committed to the leader repo, we use github actions to run bfg, which constructs a new repo that has all files/folders with the prefix "fb_" stripped out.

We then can push this repo into the follower repo, which will work correctly as the rewritten repo will only differ from the follower repo in the newest commits.


This demo repo is currently pushing into a branch in the same repo, but the idea extends to remote repos if you use a github personal access token.

