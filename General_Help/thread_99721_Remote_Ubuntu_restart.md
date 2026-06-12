---
title: "Remote Ubuntu restart"
date: 2005-12-06
forum: General Help
---

### Post by ScreemingBlue on 2005-12-06
Does anyone know how I can restart my Ubuntu box remotely. I can initiate a remote ssh session, no problem. Is there a command I can use to restart my Ubuntu box from the ssh terminal window?

Cheers

---

### Post by kosmic on 2005-12-06
yes after logged in with you SSH account, become root or use sudo and issue the following comand :
 
reboot

---

### Post by fourchannel on 2005-12-06
yes, there a few actually. but you need root permissions.

so you would SSH in and use sudo, here are a few ways to restart your comp:

```
sudo reboot
sudo halt -r
sudo shutdown -r now
``` 
i prefer the ```
shutdown -r now
``` command. just make sure you don't leave off the 'now' or it will get confused about *when* you want to reboot

---

### Post by ScreemingBlue on 2005-12-06
Ahhh, I was trying restart. Thanks for that.

---

### Post by ScreemingBlue on 2005-12-06
Thanks again....
I read somewhere about using init 1,2,3,4,5 or 6. Can these be used over SSH and what does each one do and are they specific to each distro?

Cheers

---

### Post by kosmic on 2005-12-06
[CENTER]
[CENTER] [/CENTER]

[/CENTER]

 
 
0 Halt
1 Single-user mode
2 Not used (user-definable)
3 Full multi-user mode (no GUI interface)
4 Not used (user-definable)
5 Full multiuser mode (with GUI interface)
6 Reboot

---

### Post by ScreemingBlue on 2005-12-06
[QUOTE=kosmic][CENTER]
[CENTER] [/CENTER]

[/CENTER]

 
 
0 Halt
1 Single-user mode
2 Not used (user-definable)
3 Full multi-user mode (no GUI interface)
4 Not used (user-definable)
5 Full multiuser mode (with GUI interface)
6 Reboot[/QUOTE]

Cheers for that. Can these be used through a SSH session?

---

### Post by kosmic on 2005-12-06
yes just do as root or using sudo :
 
sudo init 1
 
or sudo init 6

---

### Post by steve.horsley on 2005-12-06
[QUOTE=kosmic][CENTER]
[CENTER] [/CENTER]

[/CENTER]

 
 
0 Halt
1 Single-user mode
2 Not used (user-definable)
3 Full multi-user mode (no GUI interface)
4 Not used (user-definable)
5 Full multiuser mode (with GUI interface)
6 Reboot[/QUOTE]

I think these are the red-hat uses. I believe that in Ubuntu, levels 2-5 are configured identically with 2 being the default. That said, init 0 shuts the machine down, and init 6 reboots it which is what was being asked.

Steve

---

### Post by Sjun on 2005-12-22
The problem that i'm having here is that after bootup i can't login on either vnc or ssh, untill i login with some useraccount on the local machine.
Suppose i could set some account to login automatically after x-seconds, but that is something i rather would not.

Is there some setting i have missed, or is this default behaviour i cannot workaround easily?

---

### Post by rcerreto on 2005-12-22
That's not a default behaviour.
ssh should work.

My guess is that sshd is not started at boot time and that it gets then started by vnc.

You should have a shell script named 'ssh' in /etc/init.d and a symbolic link named S20ssh (or something similar) in /etc/rc2.d pointing to it.
If not, maybe we know what's going wrong.

---

