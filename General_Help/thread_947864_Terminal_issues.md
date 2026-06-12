---
title: "Terminal issues"
date: 2008-10-14
forum: General Help
---

### Post by robobot on 2008-10-14
I'm having some issues with the terminal. They happen with any terminal program I try to use.

First, it doesn't display anything before the "$" on the line with the cursor.

Second, when I press some keys, it responds incorrectly. For example, when I press the up arrow, it types "^[[A" instead of displaying the last command entered. I have tried changing keyboard input settings, but this doesn't fix anything. The keyboard works properly for everything else.

---

### Post by tCarls on 2008-10-14
It sounds like you're using a very limited shell. If you run "bash" does it get better? Can you post the output of the following?

```

$ echo $SHELL
$ ls -l /bin/sh

```

---

### Post by robobot on 2008-10-14
If I run "bash", it fixes everything. Thanks.

---

### Post by Sam on 2008-10-14
Try this:```
sudo usermod --shell /bin/bash $USER
```

---

