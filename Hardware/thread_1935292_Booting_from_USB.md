---
title: "Booting from USB"
date: 2012-03-04
forum: Hardware
---

### Post by Commandrkeen on 2012-03-04
I am trying to follow [this]("https://help.ubuntu.com/community/BootFromUSB") guide but it's not working so well. I press 'c' and go into the command line interface to try and search for the USB device but the 'root' command doesn't work. I get "error: unknown command 'root'." So not sure what to do. I typed in 'help' but a small list of commands that don't seem to help show up.

I am on a Macbook Pro 2008 with a triple partitioned hdd with Mac OS 10.6 Windows 7 and Ubuntu 11.10. Thanks :)

---

### Post by codemaniac on 2012-03-04
Hello mate,

I guess you are trying to boot from a bootable ubuntu usb stick .
When you start you system , go to system BIOS setting and select something like boot from USB .then save and restart your system .

Cheers

---

### Post by Commandrkeen on 2012-03-04
Thanks man,

The thing is is that I am booting from rEFIt on my Macbook Pro. So when I go to the USB stick and select it. It goes to the Ubuntu/Winows 7 GRUB instead of the USB stick. So I need to use the command line from the GRUB by hitting 'c' and using the root command. But, the root command doesn't exist I have to add it to the GRUB configuration. I am looking around and can't find anything about how to add commands to the GRUB menu.lst file or grub.cfg file. :(

---

### Post by codemaniac on 2012-03-04
Have you prepared [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick")your Ubuntu USB stick before using .
Please have a look at this .

---

### Post by Commandrkeen on 2012-03-04
Yeah I set it up alright. It works on my desktop just fine. I just need someone to tell me how to add commands to the GRUB configuration. I emailed dedoimedo about it so if I hear back from him first I'll post it and mark it solved. Thanks :)

---

