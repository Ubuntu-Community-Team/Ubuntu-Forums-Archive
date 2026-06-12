---
title: "Sudo problem"
date: 2008-11-04
forum: General Help
---

### Post by cenoura on 2008-11-04
Hy there,
I'm having a strange problem... my sudo don't accept my password.
I can reboot, login with my user name and pass but when I go to the console it keeps telling me the password is incorrect

Any hints?
Thanks in advance

---

### Post by DGortze380 on 2008-11-04
> **cenoura said:**
> Hy there,
I'm having a strange problem... my sudo don't accept my password.
I can reboot, login with my user name and pass but when I go to the console it keeps telling me the password is incorrect

Any hints?
Thanks in advance

Please post the exact error message you're getting.

---

### Post by bodhi.zazen on 2008-11-04
sudo uses the same password you use to log in. As you type your password you will not see anything reflected in the terminal. This is normal.

---

### Post by cenoura on 2008-11-04
> **DGortze380 said:**
> Please post the exact error message you're getting.

joao@cenLinux:~$ sudo ifconfig eth0 192.168.0.1 255.255.255.0
[sudo] password for joao: 
Sorry, try again.
[sudo] password for joao: 
Sorry, try again.
[sudo] password for joao: 
Sorry, try again.
sudo: 3 incorrect password attempts
joao@cenLinux:~$ 


> **bodhi.zazen said:**
> sudo uses the same password you use to log in. As you type your password you will not see anything reflected in the terminal. This is normal.

yeah I know how sudo works... I've been using sudo normally (it was working) but now it rejects my password... thats the strange part, because I can login but can't use my password on sudo. 

I've also typed the command "id" on the console and I'm in the groups admin and adm

---

### Post by DGortze380 on 2008-11-04
> **cenoura said:**
> joao@cenLinux:~$ sudo ifconfig eth0 192.168.0.1 255.255.255.0
[sudo] password for joao: 
Sorry, try again.
[sudo] password for joao: 
Sorry, try again.
[sudo] password for joao: 
Sorry, try again.
sudo: 3 incorrect password attempts
joao@cenLinux:~$ 




yeah I know how sudo works... I've been using sudo normally (it was working) but now it rejects my password... thats the strange part, because I can login but can't use my password on sudo. 

I've also typed the command "id" on the console and I'm in the groups admin and adm

try changing your password

```

passwd

```

note: it's advisable to create a new user with admin and sudo privileges before attempting to fix problems with sudo

---

### Post by cenoura on 2008-11-04
> **DGortze380 said:**
> try changing your password

```

passwd

```

note: it's advisable to create a new user with admin and sudo privileges before attempting to fix problems with sudo

I've tried that to... still not working:confused:
Can add a new user without permissions?! I can't even open synaptics, because it doesn't accept my password =\
(just in case, i've checked caps, num lock... I'm putting the same password that i've used to login)
weird...

---

### Post by taurus on 2008-11-04
Are you the original user that was created during the installing process?

---

### Post by DGortze380 on 2008-11-04
> **cenoura said:**
> I've tried that to... still not working:confused:
Can add a new user without permissions?! I can't even open synaptics, because it doesn't accept my password =\
(just in case, i've checked caps, num lock... I'm putting the same password that i've used to login)
weird...

The error messages lead me to believe that you're typing your password incorrectly. But if you're sure you're typing it correct...

try booting into recovery mode and resetting your password.

---

### Post by aysiu on 2008-11-04
Any chance you have Caps Lock on?

---

### Post by sisco311 on 2008-11-04
can you use your password in the virtual terminal?

press Ctrl+Alt+F1, log in and try to use sudo
press Ctrl+Alt+F7 to switch back to the gui.

did you change the keyboard layout?

---

### Post by cenoura on 2008-11-04
> **taurus said:**
> Are you the original user that was created during the installing process?
Yes, actually its the only user registered in this computer


> **DGortze380 said:**
> The error messages lead me to believe that you're typing your password incorrectly. But if you're sure you're typing it correct...

try booting into recovery mode and resetting your password.
How do I reset my password?


> **aysiu said:**
> Any chance you have Caps Lock on?
I wish I had=P unfortunately I dont (also tried gksudo, it warns if caps are on)


> **sisco311 said:**
> can you use your password in the virtual terminal?

press Ctrl+Alt+F1, log in and try to use sudo
press Ctrl+Alt+F7 to switch back to the gui.

did you change the keyboard layout?
No. I can login with my username and password, but when I use sudo, same problem=(


Thanks for the all fast replies

---

### Post by DGortze380 on 2008-11-04
> **cenoura said:**
> 
How do I reset my password?


reboot, choose recovery mode from the GRUB list, when you get to a root shell type 'passwd <username>' without the quotes, replace <> with your username.

---

### Post by taurus on 2008-11-04
If changing to a new password still doesn't work with sudo, post the output of this command here then.

```
id
```

---

### Post by cenoura on 2008-11-04
> **DGortze380 said:**
> reboot, choose recovery mode from the GRUB list, when you get to a root shell type 'passwd <username>' without the quotes, replace <> with your username.
I've set the passwd for my username (joao) and root. sudo still not working=( and if I try su - I cant use the passwd that I setted for root

> **taurus said:**
> If changing to a new password still doesn't work with sudo, post the output of this command here then.

```
id
```
joao@cenLinux:~$ id
uid=1000(joao) gid=1000(joao) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(joao)

---

### Post by taurus on 2008-11-04
Did you play around with your /etc/sudoers?

---

### Post by cenoura on 2008-11-04
> **taurus said:**
> Did you play around with your /etc/sudoers?
No. But I've been google around and found something about it. I'm going to cat that file and post the output

---

### Post by cenoura on 2008-11-04
> **taurus said:**
> Did you play around with your /etc/sudoers?
Ok, the sudoers w/out comments:
Defaults      env_reset
root          ALL=(ALL) ALL
%admin        ALL=(ALL) ALL

---

### Post by sisco311 on 2008-11-04
the sudoers file looks ok.

what keyboard layout are you using?

please post the output of:
```
setxkbmap -print
```

---

### Post by DGortze380 on 2008-11-04
> **cenoura said:**
> Ok, the sudoers w/out comments:
Defaults      env_reset
root          ALL=(ALL) ALL
%admin        ALL=(ALL) ALL

That's about what's expected. It's odd that your username isn't there, but you're in admin, so it shouldn't be an issue. You can try adding the following line to sudoers: joao   ALL=(ALL) ALL

PLEASE, POST HERE FOR FURTHER INSTRUCTION BEFORE EDITING SUDOERS! YOU CAN EASILY FRY YOUR SYSTEM.

---

### Post by Halfling Rogue on 2008-11-04
If you log out of Ubuntu without shutting down, does it let you log back in with the password?

---

### Post by aysiu on 2008-11-04
This is what the default /etc/sudoers file looks like: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

**Defaults	env_reset**

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
**root	ALL=(ALL) ALL**

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) NOPASSWD: ALL**
``` You may also want to double-check your /etc/groups file and make sure your user is in the *admin* group.

---

### Post by cenoura on 2008-11-04
> **sisco311 said:**
> the sudoers file looks ok.

what keyboard layout are you using?

please post the output of:
```
setxkbmap -print
```
joao@joao-desktop:~$ setxkbmap -print
```
xkb_keymap {
	xkb_keycodes  { include "xfree86+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+pt+level3(ralt_switch_for_alts_toggle)+group(alts_toggle)"	};
	xkb_geometry  { include "pc(pc105)"	};
};
```
I'm using a portuguese layout (pc105

> **DGortze380 said:**
> You can try adding the following line to sudoers: joao   ALL=(ALL) ALL
Done, although didn't work=( went to the recovery mode and visudo /etc/sudoers... back to the system and still the same 

> **Halfling Rogue said:**
> If you log out of Ubuntu without shutting down, does it let you log back in with the password?
Yes, I'm able to logout and login several times (like tried 3 times=P)

I have to go now, tomorrow I'll check this thread again
Once more, thanks for the feedback and hope to see more hints

---

### Post by sisco311 on 2008-11-04
can you use your password with sudo if you switch to the us layout?
```
setxkbmap us
```

@aysiu

the default sudoers file looks like:
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**

---

