---
title: "Ubuntu Dead after install - just grey screen and drums"
date: 2008-10-31
forum: General Help
---

### Post by rbtyod on 2008-10-31
I installed Ubuntu 8.10 through Wubi and got no error messages on the install on my 2.4Ghz Compaq Presario 6000 that runs XP with all current updates.

When I try to run Ubuntu I see the Ubuntu progress bar and then I get to a plain, light grey blank screen and nothing more happens.

If I press the ESC key I hear drums. A few other keys produce a soft beep or buzz. There is no cursor. (Luckily, I can still boot XP with no problem.)

After searching in the forums I found a suggestion  to run chkdsk/r in Windows and then reboot Ubuntu. I did this. It took about 2 1/2 hours to run chkdsk/r but it made no difference.

...Bob  :(

PS   I have my machine set up to use 2 monitors in XP

---

### Post by ago on 2008-10-31
that is probably due to video driver issues

press esc at boot after "ubuntu" and go for recovery mode, you can fix X from there

---

### Post by rbtyod on 2008-10-31
Thanks, ago, for your reply. I did as you suggested (I think) but there was no noticable change except that my 2nd monitor now has a kind of vertical striped noise pattern on it. Main monitor still has grey screen and ESC gives drums. More keys now give beep/buzz.

After selectin fix X I selected "resume normal boot". I also tried rebooting from scratch. Results were the same for both.

...Bob

In addition, I also tried shutting off my newer graphics card and monitor and using just the older ones in XP. This seemed to make no difference when booting Ubuntu.

---

### Post by ago on 2008-11-03
You might have to configure it manually. There are several guides on the internet. Start searching these forums for the make and model of your video card.

---

