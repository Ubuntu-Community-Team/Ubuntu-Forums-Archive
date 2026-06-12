---
title: "not typing a password every time you sudo"
date: 2005-11-18
forum: General Help
---

### Post by kcthomas on 2005-11-18
Hi, is there a way that you can save the root password during a session.  right now every time i run something that needs root privileges i have to type the password.  it would be nice to only type it once and then not have to type it until i log out.  im not really woried about security issues, im the only one who uses this computer.

---

### Post by Clazzy on 2005-11-18
Just type sudo -s and leave the terminal window open?

---

### Post by Joe_lurker on 2005-11-18
Use the command visudo to modify the /etc/sudoers files.  Find the line:
```
%admin  ALL=(ALL) ALL
```
and change it to:
```
%admin  ALL=NOPASSWORD: ALL
```
This will make it so you don't need a password for sudo.

-Joe

---

### Post by aysiu on 2005-11-18
How about a launcher with this command? ```
gksudo nautilus
```

---

### Post by Kyral on 2005-11-18
[QUOTE=Joe_lurker]Use the command visudo to modify the /etc/sudoers files.  Find the line:
```
%admin  ALL=(ALL) ALL
```
and change it to:
```
%admin  ALL=NOPASSWORD: ALL
```
This will make it so you don't need a password for sudo.

-Joe[/QUOTE]
No offense dude, but that is one of the worst pieces of advice I have seen. You just disabled all security that sudo provides and have effectively made the user root all the time. Please please please please don't advocate this. I am begging you. Please.

There is a reason you have to put in your password. Think about that

---

### Post by Joe_lurker on 2005-11-18
Agreed, but if a person wants to disable their security that's their own concern.  There may be reasons that somebody might want to do this.  That is why it is there.  I myself would never disable the passwords like this.

I am not advocating it just passing showing an option.

-Joe

---

### Post by aysiu on 2005-11-18
But kcthomas wants to type the password in only one time, not zero times.

---

### Post by Kyral on 2005-11-18
The way sudo works is that once you sudo once, a timestamp is created. The timestamp will expire in 15 minutes. During that time you can use sudo without typing your password. Of course if you close your terminal it also expires. Keep in mind this also applies to the GUI apps, since technically they spawn from tty7.

---

### Post by Joe_lurker on 2005-11-18
You can change the timestamp_timeout in the /etc/sudoers file to a higher value.  If you set it for 1440 minutes (24 hours) then it should only prompt you once a day or if you log off.

There is also a way to share the timestamp thoughout sessions but I can't remember how to do it off the top of my head.  Using a shared timestamp opening a new terminal should not prompt you for a password if it's within the timestamp period.

Just remember to think security.  Some of the stuff in this thread can be used to subvert the security of your system. (for kyral :))

-Joe

---

### Post by bertilow on 2005-11-18
[QUOTE=Kyral]You just disabled all security that sudo provides and have effectively made the user root all the time. Please please please please don't advocate this.[/QUOTE]

I guess you're right. But could you please explain to me why my system behaves just that insecurely although my sudoers file has "ALL=(ALL) ALL" at my name?

I have no idea what setting makes it so, but I never need to type my password. If I use a console window, I just need to type "sudo", and then I can do anything. If I launch e.g. Synaptic (in KDE) just clicking an icon, or choosing "Aministrator mode" in "System Settings", I get to do anything without providing a password.

Surely something is wrong here. This started when I installed Breezy (Kubuntu). When I did that the installer also made me create a root account, although that should not happen in Ubuntu. I chose "Expert mode" in the installation, but that should not really make that kind of a difference. After the installation I couldn't use "sudo" at all. It turned out that I had not been added to the sudoers file. I had to add myself manually - from the "root" account that should not exist! I added "ALL=(ALL) ALL", and since then I can do anything without providing a password.

Actually I can change the behaviour of Synaptic. In the KDE menu editor  Synaptic (for some reason) has "Run as a different user" checked (but no user name specified!). If I remove that checkmark, Synaptic just tells me I need to run it as root. I does not however let me type in a password (but just quits)!

Obviously my system is not in order. But how can I change it to the better?

Actually I'm convinced that Breezy is severly broken, but I'm not in the mood to spend yet another week or more to reinstall it (or another distro) and getting all my applications up to speed. But these security concerns really have me worried.

Please help!

---

### Post by ardchoille on 2005-11-27
I would like to make sudo stop asking me for my password.
Here is my sudoers file:

```

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
my_username  ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%adm    ALL=(ALL) NOPASSWD: ALL
%admin  ALL=(ALL) ALL

```

I am in group adm. Can anyone tell what is wrong with the above?

---

### Post by tomwell on 2005-11-27
why do you want to do this?? its quite dangerous to run as superuser...Possibe but dangerous...

---

### Post by ardchoille on 2005-11-27
[QUOTE=tomwell]why do you want to do this?? its quite dangerous to run as superuser...Possibe but dangerous...[/QUOTE]
It's no different than typing your password and running the desired app/command. I am just bypassing the step that requires me to type in a password that I already know in order to be able to do something that I should be able to do in the first place. What is the difference between the following scenarios?

Scenario 1:
1) I type "sudo visudo"
2) I have to enter my password
3) I can now edit the sudoers file


Scenario 2:
1) I type "sudo visudo"
2) I can now edit the sudoers file

I already know the password and no one else has access to this box. I am just trying to eliminate an unnecessary step.

---

### Post by ardchoille on 2005-11-27
How do I get sudo to stop asking me for my password?

---

### Post by aysiu on 2005-11-27
I merged this with another thread from last week--as you can see, this gets asked a lot. The answer is there if you want it, but so are the caution warnings. You may want to read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) in full to see what all the reasons were for implementing this security system. If you don't agree, then do whatever you want, but you should at least understand why it's set up this way.

---

