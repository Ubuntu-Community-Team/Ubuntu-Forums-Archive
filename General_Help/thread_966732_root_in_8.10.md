---
title: "root in 8.10"
date: 2008-11-01
forum: General Help
---

### Post by Malamut on 2008-11-01
I have installed Intrepid today and found that all GNOME applications have a lot of problems running in root account. For example, gedit send errors like ```
GConft system error...
``` I seems that ubuntu developers forgot to add GNOME local settings to root account :evil: Unfortunately (or rather luckily) I can't work without root account. How can I make it useable?

---

### Post by snova on 2008-11-01
Are you using sudo? Try using gksudo instead in this case.

---

### Post by eotakos on 2008-11-01
ubuntu is built to work with the sudo prefix for the commands that need root previleges. Furthermore, it is highly recommended that you stick with it. Sudo is very flexible though, and you can adjust the way it works. 

You can visit
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
to find out how

---

### Post by Malamut on 2008-11-01
I know about sudo))) But, as I wrote, I need root account. In 8.04 there were not any problems with it. In 8.10 command **su** work very strange... I try to enable login with root account, then restart, login as root, and all works without any errors. If I use **sudo** or **sudo su** all works perfectly. But if I use only **su** there are a lot of errors. Well, I can use sudo su instead su, but now I'm really interesting in why it works so strange?

---

### Post by eotakos on 2008-11-01
if you need the root account in the console, you can also

sudo gnome-terminal


why things work this way, i can't answer you that, maybe another user with lots of creamy coffees in his coffee stack could

---

### Post by cariboo on 2008-11-01
I can't say why the OP is getting error messages, but if you use:

```
sudo -i
```

that drop's you to a root shell, you can run as root as long as you want.

Any gnome configuration changes you make as root, will only work for root, each user has their own configuration files in their own home directory

Jim

---

### Post by Malamut on 2008-11-01
> **cariboo907 said:**
> I can't say why the OP is getting error messages, but if you use:

```
sudo -i
```

that drop's you to a root shell, you can run as root as long as you want.

Jim
Yes, **sudo su** works the same way as **sudo -i**. You can write to .bashrc alias su='sudo su' (or 'sudo -i') and all will work as in 8.04.
But may be somebody know why **su** (without sudo) doesn't work (only for the love of the game :popcorn:)

---

### Post by Malamut on 2008-11-01
> **cariboo907 said:**
> 
Any gnome configuration changes you make as root, will only work for root, each user has their own configuration files in their own home directory
I understand it, but I can't understand why at that time **su** doesn't work!

---

### Post by bab1 on 2008-11-01
I believe sudu -i uses the users authentication to allow the root shell.  On the other hand su (switch user) needs the root account password.  I have a root password and su works perfectly.

---

### Post by Nepherte on 2008-11-01
> **Malamut said:**
> I understand it, but I can't understand why at that time **su** doesn't work!
su is to switch to another user. The root user is disabled in a default ubuntu install (and just keep it that way!) so it's kinda logical it doesn't work as supposed to. Sudo is a full replacement for root, so you don't need a root account at all.

---

### Post by Malamut on 2008-11-01
Unfortunatelly, I don't know english so good to write clear than I wrote above. I have used Linux for 3 year (and Ubuntu since 7.10) and I know, that su is to switch to another user (default to root), that root is disabled and instead of su you should use sudo, that su don't work in ubuntu until something like sudo passwd root. Yes, I know it. So, I can't understand difference between su and sudo su (in result). But in 8.10 there is a difference! As I wrote, after sudo su gedit start without errors, but after su it write a lot of errors.

---

### Post by bab1 on 2008-11-01
> **Nepherte said:**
> ... Sudo is a full replacement for root, so you don't need a root account at all.

This is not exactly accurate.  Sudo allows authorized users to run apps ***as ***root.  You always need a root account.  The root account is ***not*** disabled by default.  It just doesn't have a known password.

---

### Post by bab1 on 2008-11-01
> **Malamut said:**
> ...As I wrote, after sudo su gedit start without errors, but after su it write a lot of errors.
This may be due to you trying to run a GUI based app from a root shell.  I have see this failure before.  Gedit works best using  Alt-f2 and gksudo

---

### Post by Malamut on 2008-11-01
Well, gedit works best with all variant of sudo (sudo, gksu, gksudo, sudo su, sudo -i) from shell or from GUI, but can't works without sudo (with su). And I'm  extremelly interesting why.

---

### Post by bab1 on 2008-11-01
I believe that the reason has to do more with the GIO libs (new Gnome libraries) more than with gedit or with sudo or su.  So much code these days is written with the need to prevent exploits.

---

### Post by Nepherte on 2008-11-02
> **bab1 said:**
> This is not exactly accurate.  Sudo allows authorized users to run apps ***as ***root.  You always need a root account.  The root account is ***not*** disabled by default.  It just doesn't have a known password.
I'm sorry to say but root is disabled by default. The exact operation is
```
passwd -l
```
The man page says:
```
-l, --lock
           Lock the named account. This option disables an account by changing
           the password to a value which matches no possible encrypted value,
           and by setting the account expiry field to 1.
```
I agree that it doesn't have a known password. In fact, you will never be able to guess the password as it has no possible encrypted value.

---

### Post by dburnett77 on 2008-11-02
> **Malamut said:**
> I have installed Intrepid today and found that all GNOME applications have a lot of problems running in root account. For example, gedit send errors like ```
GConft system error...
``` I seems that ubuntu developers forgot to add GNOME local settings to root account :evil: Unfortunately (or rather luckily) I can't work without root account. How can I make it useable?

The GTK interface is non-root friendly, so as to thwart root access via remote.  You'll have to install the separate pkgs. of the gtk gui, for easy clickability.

Start in synaptic by menuing with gui interface.  Then, you'll get to click, whilst others pertain of interest.

---

### Post by bab1 on 2008-11-02
@Nepherte,

I believe you will find that the root account is **not** disabled.  The use of ```
passwd -l
``` disabling this  account would stop the system!  A quick look at ```
top -u root
``` reveals  that indeed the root account is active and the owner of system processes.

```
PID USER PR  NI  VIRT  RES  SHR S %CPU %MEM  TIME+ COMMAND
1 root    18   0  2948 1856  532 S  0.0   0.5  0:03.48   init
2 root    11  -5     0    0    0 S  0.0   0.0   0:00.00 kthreadd
3 root    RT  -5     0    0    0 S  0.0   0.0 0:00.00 migration/0

and so on...

```

Edit:  I think you will find passwd -l does **lock** mortal users accounts, thus stopping their use.

---

### Post by cariboo on 2008-11-02
You should be using gksu or gksudo for programs with a gui eg:

```
gksu gedit /etc/apt/menu.list
```

Jim

---

### Post by snova on 2008-11-02
> **bab1 said:**
> I believe you will find that the root account is **not** disabled.  The use of ```
passwd -l
``` disabling this  account would stop the system!  A quick look at ```
top -u root
``` reveals  that indeed the root account is active and the owner of system processes.

That doesn't mean anything. The root account *is* disabled, or locked, or whatever. You cannot login as root, period.

These processes are running as root because they were spawned by init, the first and parent of all processes. init is started directly by the kernel, with UID 0. Logging in as root never happens.

---

### Post by theacerguy on 2009-01-05
i just want to log in as him if i do it at the login screen it says super user is not allowed to login from this screen how do i log in as root?:confused:

---

### Post by snova on 2009-01-05
> **theacerguy said:**
> i just want to log in as him if i do it at the login screen it says super user is not allowed to login from this screen how do i log in as root?:confused:

You cannot. The root account is disabled.

It can be enabled, but:

[LIST]
[*]There is no reason to. sudo more than compensates for a root login.
[*]Even if you reenabled the root account, you still can't log in graphically without tweaking additional settings.
[*]Enabling the account is not supported on these forums. Google for it- I do not know how and you will not be taught here.
[/LIST]

---

