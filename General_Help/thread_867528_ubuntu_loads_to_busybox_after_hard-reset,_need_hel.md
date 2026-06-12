---
title: "ubuntu loads to busybox after hard-reset, need help"
date: 2008-07-22
forum: General Help
---

### Post by brianjk on 2008-07-22
Ubuntu was installed via Wubi and I used it for a few days with no problems. It froze yesterday and had to shut it down using the power switch. When it rebooted, it loaded to busybox with this message (when i loaded with no "splash quiet"):

host/ubuntu/disks/root.disk does not exist

I do have this file on my computer so I am trying to find a solution. If anyone can direct me in the right way, I would be most grateful.

---

### Post by prshah on 2008-07-23
> **brianjk said:**
>  It froze yesterday and had to shut it down using the power switch. 
host/ubuntu/disks/root.disk does not exist


Run a hard disk check in Windows: click start-run, the give the command ```
cmd
``` and press enter. In the command prompt, give the command ```
chkdsk/f c:
``` Replace c: with the drive that actually held the wubi files. You may need to restart the computer for the check to take place. If you are asked to "close open file handles" or words to that effect, choose "n", and/or when asked to check on reboot, choose "y".

Note: There is a tiny (<1%) chance that this command can cause data loss; but you should be aware that any data, if lost, would have been inaccessible in the first place. In short: running this is recommended, but at your own (minimal) risk.

---

### Post by brianjk on 2008-07-23
thanks, i gave it a try but still happens...

---

