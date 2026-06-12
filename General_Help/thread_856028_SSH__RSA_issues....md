---
title: "SSH / RSA issues..."
date: 2008-07-11
forum: General Help
---

### Post by reilus on 2008-07-11
I did this:

$ sudo ssh -D 1080 hyozan@192.168.1.101

Then it said:

Warning: Permanently added '192.168.1.101 (RSA) to the list of known hosts.

Well, I played around with the SSH tunnel, and now I want to remove this IP address from the list of known hosts. 

How do I do that?  

I tried to edit the config file, but got this error:

[I was in the proper directory when I used this command]

$ sudo gedit ssh_config
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

I'm not even sure if editing the config file will allow me to remove it from the list of known hosts or not.  

I have two questions:  

How do I remove an address from the list of known hosts?

Why won't gedit allow me edit the config file?

---

### Post by frankos44 on 2008-07-11
> **reilus said:**
> I did this:

$ sudo ssh -D 1080 hyozan@192.168.1.101

Then it said:

Warning: Permanently added '192.168.1.101 (RSA) to the list of known hosts.

Well, I played around with the SSH tunnel, and now I want to remove this IP address from the list of known hosts. 

How do I do that?  

I tried to edit the config file, but got this error:

[I was in the proper directory when I used this command]

$ sudo gedit ssh_config
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

I'm not even sure if editing the config file will allow me to remove it from the list of known hosts or not.  

I have two questions:  

How do I remove an address from the list of known hosts?

Why won't gedit allow me edit the config file?

rm ~/.ssh/*

---

### Post by reilus on 2008-07-11
That is one solution.

I was able to fix the problem, and here are two solutions I figured out:


$ sudo nano /home/USERNAME/.ssh/known_hosts

(nano lets you edit the file, you can clear out the unwanted IP)
(the path after nano describes the location of the known_hosts file)

The other solution:

$ gksudo gedit /home/USERNAME/.ssh/known_hosts

(I don't know why gksudo is preferred over sudo, but it works)
(again, the path after gedit is the location of the file)

---

### Post by bodhi.zazen on 2008-07-11
> **frankos44 said:**
> rm ~/.ssh/*

NO ....

That command will also remove other files in .ssh you might want to keep including keys,

Either 

rm ~/.ssh/known_hosts

or edit the file ...

---

### Post by frankos44 on 2008-07-11
> **bodhi.zazen said:**
> NO ....

That command will also remove other files in .ssh you might want to keep including keys,

Either 

rm ~/.ssh/known_hosts

or edit the file ...


I fully agree.... in this case however it is very unlikely he had any keys.

rm ~/.ssh/known_hosts is better.

---

### Post by bodhi.zazen on 2008-07-11
LOL, I was thinking of what would happen to me if I ran that command :lolflag:

I was just trying to post a caution to anyone who might have keys.

---

### Post by MasterXandrex on 2008-07-11
> **reilus said:**
> 
(I don't know why gksudo is preferred over sudo, but it works)


gksudo is basically the same thing but gives a graphical prompt.

Xan

---

### Post by bodhi.zazen on 2008-07-11
It has to do with running X applications as multiple users and root. X has it's own set of security. Without such security features to X you have problems such as key loggers.

So gksu gives you root access to graphical apps while maintaining security.

---

### Post by MasterXandrex on 2008-07-11
Interesting, I hadn't really considered additional levels of security take into account with that -- i'll probably use it more often now.

Xan

---

### Post by dewittdale on 2008-07-27
> **bodhi.zazen said:**
> LOL, I was thinking of what would happen to me if I ran that command :lolflag:

I was just trying to post a caution to anyone who might have keys.
So to the novice you're pointing to the fact one can delete the known_hosts file and it will regenerate when making future connections via ssh, yes?  Or would merely cutting and saving from within the file be more appropriate in terms of electron efficiency?

---

### Post by bodhi.zazen on 2008-07-28
> **dewittdale said:**
> So to the novice you're pointing to the fact one can delete the known_hosts file and it will regenerate when making future connections via ssh, yes?  Or would merely cutting and saving from within the file be more appropriate in terms of electron efficiency?

Yes, you can delete the ~/.ssh/known_hosts and it will be re-configured.

If you prefer, go ahead and edit the file, delete the host that changed.

The general idea here is that you get a warning the the server you are logging into has changed in some way. If you know it has changed, no big deal. If not, you should check with the sys admin (of the server). This eliminates "spoofing" if yo will.

---

