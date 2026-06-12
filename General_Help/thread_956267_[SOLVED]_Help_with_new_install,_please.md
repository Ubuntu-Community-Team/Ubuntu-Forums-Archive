---
title: "[SOLVED] Help with new install, please"
date: 2008-10-23
forum: General Help
---

### Post by Ironhorse_somo on 2008-10-23
Background info:
I have installed Ubuntu 8.04.1 LTS Desktop edition 32 bit as my only OS (the disc was received from Ubuntu via snail mail - not burned on my computer.) My computer was built for me by a local shop and is not any name brand. After playing with Ubuntu a little on the disc, I installed it over my existing Windows, and have no Windows any more.

The problem:
After it goes through the ubuntu startup screen, and I watch the little bar go back and forth under the ubuntu logo, it kicks up the following error:

Busybox v1.13 (Debian 1:1.1.3-5ubuntu12)Built-in shell (ash) Enter 'help' for a list of built-in commands.
(Initframs)

And I am unable to proceed any further. Yes, I am a complete newbie to Ubuntu. Help?

---

### Post by Ryadt on 2008-10-23
Try to use the kernel boot options "all_generic_ide" .
Follow this guide as to how to input the parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
substitute the "quiet splash --" and add "all_generic_ide" (without the quotes)

---

### Post by Ironhorse_somo on 2008-10-23
A million thanks, Ryadt! That did the trick!! You rock!

---

### Post by Ryadt on 2008-10-23
You're welcome.... ;)

---

### Post by Ironhorse_somo on 2008-10-23
One last question.... Is there any way to make that permanent, so I don't have to go in and edit the kernel every time I reboot the computer?

---

