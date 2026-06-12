---
title: "[SOLVED] evolution doesn't show read owa messages"
date: 2008-11-16
forum: General Help
---

### Post by moore.bryan on 2008-11-16
i had this problem before, someone kindly offered a solution, but for the life of me i can neither find nor remember it...

when i check my work email via owa and read a message, it then does not show-up in evolution at all. i know the suggestion was something along the lines of a script to delete some file in my evolution profile before it's loading.

thanks for any help!

EDIT:
[cue music, *Pink Floyd*] is there anybody out there?

EDIT 2:
[cue music, *KT Tunstall*] finally, i see...
the answer was deep in my gmail from the evolution team; just needed to create a small script to clean things-up:
```

#!/bin/bash
evolution --force-shutdown &&
rm -rf ~/.evolution/exchange/ ~/.evolution/mail/exchange/ &&
evolution

```
works like a charm for anyone else in the same situation.

---

