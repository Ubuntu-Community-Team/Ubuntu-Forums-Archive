---
title: "mount smb stops working in a script"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by ipguru99 on 2006-05-29
After upgrading to Dapper, I have learned my wife can't run her smbmount script.  This script worked before Dapper.  I have her double-click on a file that mounts a remote filesystem into her home directory.  

Now, she double-clicks the file, it asks her if she wants to display the file, run it, ..... She clicks on run it in the terminal.  It prompts her for the sudo password, as it did before, then her password for the remote share.. and there it is... except now, it locks up hard... and I mean, total FREEZE.  Really weird.

Naturally, I can browse it in Nautilus, I can even type [HTML]sudo mount -t smbfs -o hername,dmask=777,fmask=777 //deb/andrea  /home/andrea/andrea-home[/HTML].. and it works... 

I saw some other people having problems with smb stuff.. but it all looked like resolution problem...

Anybody else having a problem?

---

### Post by ipguru99 on 2006-05-30
just to make it weirder.. I installed samba on the pc I can't run the script from anymore and I get a:
[HTML]update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]

I even tried to use [HTML]sudo mount -t cifs -o user=cftw/andrea //deb/andrea /home/andrea/andrea-home[/HTML]

It works.. but now I have user andrea as uid 1001 on the server, and user andrea on the laptop as 1000... UGH.. what happened to my script?  Again.. I can type it out on the command line.. I even put the cifs script in the same file (after commenting out the smb part first ;-) and it works??

I have another machine of her's with smb stuff in the fstab.. that is working fine as well... ???

Ok, anyone else have any other ideas on how to get a smb share mounted with different uid's?  Maybe I can do it that way?

Thanks.. otherwise Dapper has rocked!!

---

### Post by ipguru99 on 2006-05-30
Becoming clearer now... 
This works
[HTML]sudo mount -t smbfs -o username=andrea //deb/andrea /home/andrea/andrea-home[/HTML]

This doesn't 
[HTML]sudo mount -t smbfs -o username=andrea,dmask=777,fmask=777 //deb/andrea /home/andrea/andrea-home[/HTML]

What changed?  I had the one with the dmask & fmask working for a year?  Now it locks up the laptop?

---

### Post by JackandJohn on 2006-06-03
You could always put the samba mounts in /etc/fstab;

Currently, there is apparently a bug that prevents automounting samba shares, so that you could have umask/filemask permissions there;

```
//<server>/<share>		/<mount point>	smbfs   uid=<id>,credentials=/home/<user>/.smbcredentials,dmask=777,fmask=777   0       0
```(note; you do need ~/.smbcredentials created and filled with:
```
username=<smb uname>
password=<smb pass>
``` )

, then run:

```
sudo mount /<mount point>
```
as the script. (or, for bonus points:
```
gksudo mount /<mount point>;nautilus /<mount point>
```(no terminal needed, and auto-browses on mount) )

---

### Post by ipguru99 on 2006-06-10
That was something someone over at launchpad told me... I tried that.. same thing.  It is really weird, too.  It is still working (in fstab) on my wife's 5.10 desktop?  

about 1/2 dozen people over at launchpad were complaining about the same thing... and kinda throwing their hands up, because nobody seemed to be listening?  I still can't do it to this day?  (She has to copy and paste it in manually.. just can't run it in a script).

Thanks for responding and sorry it took 6 days to get back.  I was actually coming back in to talk about how cups w/samba seems to be broken as well.  

Thanks...

---

### Post by acehigh on 2006-06-12
Hi all,
only to tell that I've the same problem.

---

### Post by Civil on 2006-06-13
I am having a similar problem.  I am able to browse my samba shares using Konqueror (smb://server/share), but whenever I try to mount it (either using LinNeighborhood, smb4k, bash script, or fstab), it doesn't work.  I don't get any errors while mounting, but when I try to browse to that mount point, Konqueror stalls.  Similarly, if I try to cd into the folder in a shell, I get a frozen shell.  The rest of the computer seems to run fine, but after this happens I get I/O failure on the mount point and I can't umount it because the system is busy.

Anyone have a similar problem or know what I am missing?

my fstab entry is:
```

//server/share  /home/civil/share  smbfs  defaults,uid=1000,credentials=/root/.smbcred,dmask=777,fmask=777  0  0

```

Thanks,
Civil

---

### Post by acehigh on 2006-06-14
Hi,

I added the option auto and now works.
I left the fmask and dmask as they were.
I'm going to do some tests and in the next days I'll tell if it works regularly every boot time.
Was:
```

//server/share  /home/what/you/want   smbfs   credentials=/etc/samba/xxxxx,uid=xxxx,gid=xxxxx,fmask=number,dmask=number,codepage=unicode,iocharset=utf8,unicode 0       0

```
Now:
```

//server/share  /home/what/you/want   smbfs   credentials=/etc/samba/xxxxx,uid=xxxx,gid=xxxxx,fmask=number,dmask=number,codepage=unicode,iocharset=utf8,unicode,auto 0       0

```

---

### Post by acehigh on 2006-06-15
Seems working...

---

### Post by acehigh on 2006-06-15
Ehi, look,
a new kernel available... ok, let's update the client linux box..... downloading...
a restart is suggested.... ok, let's restart... and ...


aaaaaaaaaaaaaaaarrrrrrrrrrggggggggggggggghhhhhhhhhhhhhhhhhhhhh


smb filesystems... stopped working again ............ :-x:-x:-x:-x     

grrrrrr

---

### Post by acehigh on 2006-06-21
Find the real problem [here]("https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874")

---

