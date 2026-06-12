---
title: "I'm outdated!!"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Thilo Kuhlman on 2009-03-19
I accidentally put in a 8.10 disk into Ubuntu 8.10. Now it thinks that is a source and won't let me upgrade and give me a nice good error. What sequence of keystrokes can I cram into terminal to fix my outdated software?

I will give terminal feedback on request.

Spanks,     

               ThiloK

---

### Post by Partyboi2 on 2009-03-19
Can you open a treminal and post the output to
```
sudo apt-get update
```

---

### Post by cariboo on 2009-03-19
Comment out the cdrom  entry in /etc/apt/sources.list eg:

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha amd64 (20090212)]/ jaunty main restricted
```

I'm using Jaunty, so look for Intrepid in your case.
Make sure there is a **#** at the start of the cdrom line. Then update and upgrade.

Jim

---

### Post by ubuntu27 on 2009-03-19
Go to System menu/Administration/Software Sources

On the Sofware Sources, go to the "Ubuntu Software" tab

On the button (Installable from CD-ROM/DVD) uncheck the boxes.

Click on "Close"


Now you can update your sources.

---

