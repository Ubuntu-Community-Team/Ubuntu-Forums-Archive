---
title: "Occasional garbled video after grub-pc boot"
date: 2010-02-18
forum: Hardware
---

### Post by funkiwan on 2010-02-18
I'm running grub-pc 1.97~beta4 on a laptop configured to dual boot Windows and Linux. Occasionally the screen becomes garbled after selecting Linux from the grub menu. I've attached a photo of what the screen looks like. I can login by typing the correct keystrokes and hear the Ubuntu login success audio, but the screen never ungarbles. Rebooting one or more times eventually clears the problem and I have no issues with video for the entire length of time I remain logged in.

#uname -a
Linux jgordon-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

Any ideas on what could be going wrong here? I'm not seeing any obvious errors in /var/log/messages. Anywhere else I can check?

I've attached a zipped excerpt of /var/log/messages which has the full boot with the screen errors and then followed by a successful boot.

Thanks for your help.

Jonathan

---

