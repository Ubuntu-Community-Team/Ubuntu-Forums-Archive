---
title: "can't login ubuntu cause &quot;Your Session only lasted less than 10 seconds....."
date: 2008-08-28
forum: General Help
---

### Post by rasendria on 2008-08-28
I can no longer logon to ubuntu, Hardy heron!!!! I am using 8.04. I  don't know the cause of my problem, and I don't know how to fix it. And I really don't feel like having to reinstall ubuntu and all the apps I had before, and i have so many data on my hardisk, i used 4 hardisk, @ 1 TB. I make LVM (Logical Volume Manager) to partition my hardisk  so i have 1 partition with amount 3.7 TB. The name of  that partition is " gudanglagu". 
When I use failsafe terminal mode, there is strange user.. my user is mising,.. so in terminal mode: "*I Have no name!@gudanglagu:$...*" ???

When I login to Failsafe GNOME, it just freezes and causes me to shut the computer down through brute force. Any other attempt to login gives me something like this:

*'Your session only lasted less than 10 seconds. If you have note logged out yourself,this could meant that there is some installing problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem'*

Here are the /.xsession-errors details: 

[I]/etc/gdm/xsession: Beginning session setup...
setting IM through im-switch for locale=en_us.
Start IM through /etc/X11/xinput.d/all_ALL linked /etc/x11/xinit/xinput.d/default.

(seahorse-agent:7713) GLib Warning **: getpwuid_r(): failed due to: permission denied.

(process: 7713): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.

(gconf-sanity-check-2:7764): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.
SESSION_MANAGER=local/gudanglagu:/tmp/.ICE-unix/7713[/I]


what should i do? anyone help please...
thank you for any help

---

### Post by iaculallad on 2008-08-28
Probably, you don't own the .ICEauthority file anymore or had been altered. Boot from Recovery Mode and input the command below:

```
chown your_username /home/your_username/.ICEauthority
chmod 600 /home/your_username/.ICEauthority
```

and Restart:

```
shutdown -r now
```

---

### Post by rasendria on 2008-08-29
Thanks iaculallad... but it's not work for me.
i still couldn't login.
any else idea please...

---

### Post by aloshbennett on 2008-08-29
From failsafe mode, can you try whoami and 'su gudanglagu'

---

### Post by p_quarles on 2008-08-29
My recollection is that this is a ~/.dmrc issue rather than an ~/.ICEauthority issue. Repeat the steps listed above but replace the filename above with .dmrc. 

If that doesn't work, try simply deleting .dmrc. It will auto-generate a new one.

---

### Post by rasendria on 2008-08-29
aloshbennett ---> when i type whoami. result is: cannot find name for user ID 1000.

p_quarles ---> its still couldn't work for me.
 and after that my ~/.xsession-error file be:
[I]
/etc/gdm/xsession: Beginning session setup...
setting IM through im-switch for locale=en_us.
Start IM through /etc/X11/xinput.d/all_ALL linked /etc/x11/xinit/xinput.d/default.

(seahorse-agent:7713) GLib Warning **: getpwuid_r(): failed due to: permission denied.

(process: 7713): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.

(gconf-sanity-check-2:7764): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.
SESSION_MANAGER=local/gudanglagu:/tmp/.ICE-unix/6506
Could not get password database information for UID of current process: User '???' unknown or no memory to allocate password entry.

failed to start message bius: memory allocation failure in message bus
dbus-daemon exited unexpectedly
**
** ERROR: (gsm-dbus.c:118): gsm_dbus_daemon_start: assertion failed: (dbus_daemon_pid != 0).[/I]

i'm very.. very confused.. and I really don't feel like having to reinstall ubuntu because i have so many data..
 help me pleasee.. i'm newbie for this...:-(

---

### Post by winbutu on 2008-08-29
re-install?

---

### Post by p_quarles on 2008-08-29
> **winbutu said:**
> re-install?
That's not helpful. :)

---

### Post by rasendria on 2008-08-29
> **winbutu said:**
> re-install?

its impossible to do, because right now i have 2.5 TB data(music)..:(
:confused::confused:

---

### Post by rasendria on 2008-08-29
haloo... where is the masters?? help me please...
i have looking for to solve this problem along 7 hours, but its not done..:(

---

### Post by rasendria on 2008-08-30
guys.. help me please....

---

### Post by emredmrl on 2008-10-02
I get a similar error. Did anyone find any solutions?

---

### Post by jsacks on 2008-10-14
same problem.  can anyone help?

---

### Post by manuzza on 2008-10-14
Bump. Same here. Laptop booted fine, Ubuntu installed some updates and I let it. I now have the problems described in this thread.

None of the suggestions made by anyone helps.

.xsession_errors 
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

** (seahorse-agent:6929): CRITICAL **: can't create directory: /tmp/seahorse-o3HXiF: Too many links
```

The /tmp dir has only three files in it, lots of disk space left.

Suggestions?

Manuzza.

---

### Post by AlexBellisBrown on 2008-10-14
This seems tough, but ill tell you what i would do. :popcorn:

Get yourself the Ubuntu Live CD, boot into it, and copy everything you have onto an external HDD, (Granted, 2.5TB is alot, but i have several HHDs, im hoping you do too) then do a reinstall if you cant fix the problem every other way. Give this a try as a last resort, as it is alot of work. But if its the data you worry about, dont, its still there, and the way to get at it is via the Live CD. :)

Hope it helps to know that!:)

---

### Post by AlexBellisBrown on 2008-10-14
You could also try running updates from the Failsafe terminal. (May only work if you are connected to the internet via Ethernet, wireless and terminal sometimes dont mix).

sudo apt-get update

Failing that, you could try and reinstall Ubuntu, BUT!! I dont know weather this would leave your data intact, if someone knows, please give him permission to use this:

sudo apt-get install ubuntu-desktop

I think it would leave your data... but im not sure, hence why i´d like a second opinion before you try it :)

---

### Post by user_linux08 on 2008-11-07
For some reason, I am having the same problem with Intrepid 8.10. Although I do get around it through "GNOME failsafe" option. It still a problem which hopefully someone will find a solution for.

I like to advise the poster with "2.5TB of data". Why not pratition the disk(s), such that the "/Home" is loaded onto its own logic Drive or Hard Drive. This way, all needed to re-install is only the OS itself. Make sure though, during the re-installations to a) point the root directory to the "/" partition, and b) point the "/home" partition to the original Home drive WITH NO FORMATTING. 

Another crucial element. I wish ubuntu would have the same option of "restore" which Fedora provides. when you insert the Live-CD, there should be an option for the disk to inspect the directories on HD and restore any file which it feels has been corrupted.

---

### Post by user_linux08 on 2008-11-10
Please, any takers to the .xsession problem?.
appreciate more inputs

---

### Post by HyperHacker on 2008-11-10
Assuming your /home is on its own partition, you can reinstall without losing data. Do manual partitioning, mount that partition as /home, and don't mark it for formatting.

If it's not a separate partition, I don't know if you can do that or not.

---

### Post by gpongo on 2009-01-21
I've just run into the same problem, after upgrading from Fiesty Fawn all the way up to Hardy Huron to use newer hardware. Can't run gnome or kde because seahorse-agent reports the exact same getpwuid_r() error, giving me the same error as noted previously. I can use FVWM, however. When I ssh into the system from another computer, it thinks I am uid 1000 (the system was once debian).

The problem seems to be a dbus/hald problem-- when I execute
/etc/init.d/dbus restart, it hangs when trying to start the hardware abstraction layer... it is having trouble with some piece of my hardware, I think.

Under FVWM, whoami reports "whoami: cannot find name for user ID 1000".

gdm reports the following in ~/.xsession-errors:
[I]Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(seahorse-agent:5987): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.
[/I]
After that the fvwm messages start, whereas under kde and gnome, additional getpwuid_r() errors are reported for other modules, and then the startup attempt ends.

---

