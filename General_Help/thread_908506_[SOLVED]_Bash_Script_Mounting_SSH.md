---
title: "[SOLVED] Bash Script Mounting SSH"
date: 2008-09-02
forum: General Help
---

### Post by iamcowdrunk on 2008-09-02
I have a working script to mount(if not mounted) or unmount(if mounted) ssh by checking to see if a text file named '.mount.txt' exists. I feel like its a really sketchy way to get it done though. What I want to do is use /etc/mtab to check if its mounted but I can't seem to get it to work and I don't quite have the know-how to fix it. If anyone knows what is wrong with my script would they be so kind to assist me in fixing it?

```
#!/bin/bash

if [ grep -c 'Videos' /etc/mtab == 0 ]
then
sshfs #MY#IP#:/home/dan/Videos ~/Videos
else
fusermount -u ~/Videos
fi
```

Whatever I do I seem to get a too many arguments error.

---

### Post by Mister.Vash on 2008-09-03
grep isn't executing, try this instead

```

#!/bin/bash

if grep -c 'Videos' /etc/mtab
then
sshfs #MY#IP#:/home/dan/Videos ~/Videos
else
fusermount -u ~/Videos
fi

```

---

### Post by iamcowdrunk on 2008-09-03
Thank you sir.

---

