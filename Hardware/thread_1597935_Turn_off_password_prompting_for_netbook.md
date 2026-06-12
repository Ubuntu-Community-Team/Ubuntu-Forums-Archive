---
title: "Turn off password prompting for netbook"
date: 2010-10-15
forum: Hardware
---

### Post by jonathanhayward on 2010-10-15
After installation, how do I turn off password prompting for a 10.10 Ubuntu Netbook Remix install?

---

### Post by shahdharmit on 2010-10-15
> **jonathanhayward said:**
> After installation, how do I turn off password prompting for a 10.10 Ubuntu Netbook Remix install?

Open your /etc/passwd file in your favorite text editor. ```
sudo gedit /etc/passwd
```

The line concerned to the user I use on my machine reads like this ```
dharmit:x:1000:1000:Dharmit Shah,,,:/home/dharmit:/bin/bash
```

Find the line concerned to you in this file. From this line, remove x that appears after the username. That's it. This works for me on my laptop. I haven't tried on netbook. But steps should be same, I guess.

---

### Post by garvinrick4 on 2010-10-15
You can give it a time like 20 minutes or 30 minute or no time limit per session.
```
gksudo gedit /etc/sudoers
```#Find defaults line below 
```
Defaults    env_reset
```#make it look like this.
```
Defaults    env_reset,timestamp_timeout=-1
```#If you choose a time limit put in say 20 where -1 is and it will be 20 minutes, 30 for 30 #minutes ans so on and -1 for unlimited.

---

### Post by jonathanhayward on 2010-10-16
Thank you; I realized I'd asked a bit sloppily.

On my previous Xandros distribution, the default user logged in etc. without a password, but did have a password needed to shell in to the system.

Is there a way I can turn off password prompting on login, and on unlocking the screen, while retaining password prompting for ssh access?

---

### Post by Jay Car on 2010-10-16
> **jonathanhayward said:**
> Is there a way I can turn off password prompting on login, and on unlocking the screen, while retaining password prompting for ssh access?

Look under System> Preferences > screensaver. The default setting is to lock the screen and require a password after resuming. It's easy to change.

---

### Post by sisco311 on 2010-10-16
> **jonathanhayward said:**
> Thank you; I realized I'd asked a bit sloppily.

On my previous Xandros distribution, the default user logged in etc. without a password, but did have a password needed to shell in to the system.

Is there a way I can turn off password prompting on login, and on unlocking the screen, while retaining password prompting for ssh access?

You can enable automatic login: System -> Administration -> Login Screen

or turn off the password prompting on login: System -> Administration -> Users and Groups -> Select your user -> Password -> Change -> select *Don't ask for password on login*.

---

### Post by jonathanhayward on 2010-10-16
Thank you for pointing me to "System -> Administration"

I know how to navigate there for desktop Ubuntu, but there doesn't seem to be an "Administration" under "System" on Ubuntu Netbook Remix.

How can I find the options mentioned under Ubuntu Netbook Remix?

---

### Post by sisco311 on 2010-10-16
> **jonathanhayward said:**
> Thank you for pointing me to "System -> Administration"

I know how to navigate there for desktop Ubuntu, but there doesn't seem to be an "Administration" under "System" on Ubuntu Netbook Remix.

How can I find the options mentioned under Ubuntu Netbook Remix?

No idea. =)

The command for *Login Screen* is:
```
gdmsetup
```
and for *Users & Groups* is:
```
users-admin
```

the later method simply adds your user in the **nopasswdlogin** group, so instead of using the GUI you could run:
```
sudo gpasswd -a $USER nopasswdlogin
```

---

### Post by jonathanhayward on 2010-10-16
Thank you. I went to the screensaver and deselected the "lock when idle" button; together with this last response, I think things are solved/

---

