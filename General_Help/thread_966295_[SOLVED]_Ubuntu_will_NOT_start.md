---
title: "[SOLVED] Ubuntu will NOT start"
date: 2008-11-01
forum: General Help
---

### Post by tokyo77 on 2008-11-01
Hi,
I have installed Ubuntu 8.04 via Wubi. A day ago I was playing around with Compiz Fusion, and it froze up when I tried to paint fire (probably my crappy graphics card). So, I had to force a shutdown. Problem is, now when I start Ubuntu, it shows some text for a split second, then goes into a blank display with a blinking line at the top (kind of like the blinking line in a word processor). Whenever I press any keys, there is a beep. Then, I have to force restart because it's not going anywhere,and it beeps again (a different kind of beep) and shuts down. Can I recover Ubuntu? I set up some stuff like Evolution and things like that, so I would rather not reinstall Ubuntu. Any help would be appreciated:)!

Just a reminder, I am dual booting XP Pro SP3 and Ubuntu Hardy Heron 8.04 on a Lenovo R61i.

---

### Post by rhcm123 on 2008-11-01
unfortunately, the only solution i found to this problem was to reinstall ubuntu. When you forced the shutdown, it irreversibly corrupted the virtual disk file in windows.

Mine was even worse off when this happened. Neither windows nor ubuntu would boot. I had to get out the windows cd and use it to rewrite the hard drive MBR. Try that, if you still have your winxp cd. use the "recover system" option which should bring you to a prompt. type in 'fixmbr' and say yes to everything. it should make windows bootable again if windows wasn't bootable. DO NOT DO THIS IF WINDOWS BOOTS. IT WILL DESTROY THE OLD MBR, PERHAPS FATALLY WOUNDING YOUR COMPUTER.

Sorry, buddy, but as far as i know the only option is to reinstall ubuntu.
You could probably get your files out if you had a live cd.

---

### Post by tokyo77 on 2008-11-01
Darn.

Well, at least Windows isn't corrupted :). I also don't have any documents whatsoever...I guess I should count myself lucky. Thanks for this help, but I'll wait a day or two to see if anyone else can come up with a good answer.

---

### Post by ago on 2008-11-03
You can often recover by running chkdsk /r from winthin windows

---

### Post by tokyo77 on 2008-11-03
Well, I reinstalled Ubuntu anyway, but thanks for the tip. I'll save it for future reference.

---

