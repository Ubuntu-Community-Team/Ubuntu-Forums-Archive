---
title: "Run custom command at the first time running after installation"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by phnhat1984 on 2009-07-26
When install to ubuntu, how can I configure so that at the first time running after installing Ubuntu OS, os will run a command which does some customed configuration. Please help me

---

### Post by wojox on 2009-07-26
Can't help you run custom configurations without knowing what they are.

Do you want to set-up the distro with your personal settings to install on other computers?

---

### Post by phnhat1984 on 2009-07-26
Thanks for soon reply, 
Let me detail. I have a script that installs apache tomcat and deploy my own web into it. So what I need is after installing Ubuntu completely, at the first running, ubuntu machine will calls this script automatically.

---

### Post by wfvoogd on 2009-07-26
So you want the installer to install the custom script and then configure the boot process to run it at (1st) boot?

It seems to me when you're able to do that you might as well let the ubuntu installer install tomcat and you're webapp....

but then, i don't know how to do either, so I'm just trying to get your wishes clear :)

cheers,

Willem

---

### Post by phnhat1984 on 2009-07-26
You got my idea. Maybe I need to modify the installer to call my script at first running. But I don't know how. Anyway, if have any solution, please share to me. Great thanks

---

### Post by wfvoogd on 2009-07-26
You're problem inspires me to have the same problem. It would indeed be nice to have a web application installer on a stick:)

maybe this sheds some light:

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

I haven't read it myself, but am going to now :)

cheers,

Willem

---

### Post by wfvoogd on 2009-07-26
Well the document seems to provide the solution:
> [B][U]
Running a Final Script[/U][/B]

You can run a script in the final part of the installation. The following example runs a script that has been copied onto the installation CD in the setup/install folder. This script runs in the target environment, thus can run python, perl, etc. - any scripting system that has been installed on the target system.

```
d-i preseed/late_command string chroot /target bash /cdrom/setup/install/settings.sh
```

Egon Ojamaa: When I tested the above command with Intrepid / 8.10 it did not work. I came up with my own command. It first copies the "finisher.sh" file to hard drive and launches it with chroot from hard drive within the system on hard drive.

```
d-i preseed/late_command string cp /cdrom/finisher/finisher.sh /target/root/; chroot /target chmod +x /root/finisher.sh; chroot /target bash /root/finisher.sh
```

Well actually this isn't a script run on first boot, but rather after install finished, so basically it should be what you need i guess...

cheers,

Willem

---

### Post by phnhat1984 on 2009-07-26
Thanks so much. I will try it now.
Cheers:D

---

