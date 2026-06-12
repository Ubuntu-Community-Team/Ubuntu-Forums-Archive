---
title: "acpid daemon started?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by silverrope on 2009-08-09
Question for the ubuntu gurus (running ubuntu 9.04). How do I know if the acpid daemon has started? I did a

ps -ef | grep acpi

and there was nothing. How do I make sure the daemon starts on booting up? There should be a /proc/acpi/event file created by the daemon, but I do not see this file on my system. Can anyone point me to any documentation on acpid?

I need this in order to get power management to work on my laptop.

Thanks in advance.

---

### Post by phillw on 2009-08-09
Odd ... I have a laptop and 

```
 ps -afe | grep acp 
```

Returned

```

phillw@piglet:~$ ps -afe | grep acp
root        11     2  0 10:55 ?        00:00:00 [kacpid]
root        12     2  0 10:55 ?        00:00:02 [kacpi_notify]
root      2220     1  0 10:56 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
111       3341  3265  0 10:56 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket

```

It may sound daft, but did u include the 'a' option ?

Phill.

---

### Post by silverrope on 2009-08-10
> **phillw said:**
> 
It may sound daft, but did u include the 'a' option ?

Phill.

Including the "a" still shows that there are no acpid processes. It is clear that the daemon has not started. I tried to execute the command:

```
sudo /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
```but that resulted in 

```
acpid: can't open /proc/acpi/event: No such file or directory

```I just installed ubuntu in another machine (a desktop IBM Netvista) and the acpid daemon is running properly there and there is a /proc/acpi/event directory. So do you know how the /proc/acpi/event is created and how I can get acpid running in my laptop (IBM Thinkpad A20m) on boot?

---

### Post by phillw on 2009-08-10
This site is dedicated to acpi -- I think that it will be best to help you - I details about running acpi & what errors may occur.

Hope it solves it for you.

[http://www.thinkwiki.org/wiki/How_to_configure_acpid](http://www.thinkwiki.org/wiki/How_to_configure_acpid)


If you are pretty sure that you're missing the acpid ... you can get it from here ....

[http://sourceforge.net/projects/acpid/](http://sourceforge.net/projects/acpid/)

It's in deb - so GDebi package installer tripped in on my system (I didn't download it, as i already have the daemon)

Regards,

Phill.

P.S. - Whilst looking into something else, there is an option when installing ubuntu to turn acpi, etc. off .....  Details are here..

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by silverrope on 2009-08-12
> **phillw said:**
> 
P.S. - Whilst looking into something else, there is an option when installing ubuntu to turn acpi, etc. off .....  Details are here..

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Ah yes thanks for the link. I put in "acpi=force" in grub's menu.lst file as instructed. That did the trick! When I rebooted and logged in, the daemon was there and the power management worked! My BIOS is the most recent (2003), but for some reason it is dated as 1999 which kept acpi from starting up.

Thanks,
silverrope

---

### Post by Duncan Williams on 2011-08-19
Don't know if this is any use to you:
[http://samwel.tk/laptop_mode/](http://samwel.tk/laptop_mode/)

---

