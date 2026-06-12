---
title: "vino won't accept passwords"
date: 2008-10-12
forum: General Help
---

### Post by goldenfri on 2008-10-12
Hi I am trying to use vnc with vino on Ubuntu Hardy and when I have a password set the vnc client will not be authenticated. It works with no password, but not with a password. Any suggestions?

I am connecting with chicken of the VNC on a mac

---

### Post by srt4play on 2008-11-03
I have the same problem, prompt for confirmation works but password doesn't. Anybody know of a solution to get password authentication to work with vino?

---

### Post by srt4play on 2008-11-03
Found the answer in [this]("http://ubuntuforums.org/showpost.php?p=5932406&postcount=6") post. The full page on javazoom.net to encode the vnc password is [here.]("http://www.javazoom.net/services/base64/base64.jsp")

The bug report for this problem is [here.]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032")

---

