---
title: "Options to access a problem PC"
date: 2008-07-24
forum: General Help
---

### Post by CaesarLike on 2008-07-24
Hi All,

Earlier I posted this prolem I am having with logining into Ubuntu.

[http://ubuntuforums.org/showthread.php?p=5452916#post5452916]("http://ubuntuforums.org/showthread.php?p=5452916#post5452916")

This got me to thinking about what the various options are to be able to quickly boot into the pc, or to access files on the it.
So I am asking the community for advice on what these options are. Below is a list of the options I can think of.  Maybe you can advice me on these options, and how to use these options where neccessary, as my knowledge of Ubuntu is a bit limited in this respect.

1). Boot into X via a safe boot:
I am assuming I can log into an X session via the CLI, by first using SU to change the user, then starting up X.
If so, what is the correct command line instructions for starting up X?
Also what is the corrent commands for later shutting it down?
I assume if I boot into X in this way I do not get the login screen?

2). Access files via SSH:
Am I correct in thinking that Ubuntu will connect to the network/internet when in safe mode?  If so, I also assume that I could then access (copy etc) files on the problem PC via SSH?

3). Mount hard drive using USB: 
I could mount the hard drive from the problem PC onto another linux machine via USB. I assume that as the hard drive is formatted with ext3, Ubuntu would have no problems mounting the drive using USB?

4) Mount the drive by installing it into another Ubuntu PC.  As with the above option, I assume that another Ubuntu machine will auto mount the drive on bootup?

Okay, well there are the options I can think of for quickly accessing a problem Ubuntu PC and its files.  Your advice on these options, along with any others you know of would be greatly appreciated.

---

### Post by ryanhaigh on 2008-07-28
1) the command ```
sudo startx
``` will allow you to login to a gui as root and no you would not get the login screen. I don't know what he correct way to stop the x session is but ussually after you have done what you want you can shutdown from the menu or commandline (the command is halt)

2) Ubuntu will not connect to the network if you boot into recovery mode, you would need to start the networking and ssh services:
```
sudo /etc/init.d/networking restart
sudo /etc/init.d ssh restart
```

3) Your only issue here might be permissions depending on what you want to do. You can always use ```
gksudo nautilus
``` to open the file manager as root and do whatever you want

4)As above

---

