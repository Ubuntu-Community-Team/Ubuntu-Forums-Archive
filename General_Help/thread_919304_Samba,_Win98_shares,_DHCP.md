---
title: "Samba, Win98 shares, DHCP"
date: 2008-09-13
forum: General Help
---

### Post by Frogbarf on 2008-09-13
I've been trying to connect a Linux machine (Ubuntu 8.04) to a network with 2 Win98 machines so they all see the shares on each other.

I've got Samba going so the Win98 machines now see, and can access r/w, the shared directory on the Ubuntu machine. From Win98. the Ubuntu shares are indistinguishable from shares on another Win machine in the same workgroup.

But on the Ubuntu side of things, I'm having trouble. It might be fair to say I'm suffering intellectual indigestion from too much knowledge and too many options.

[In what follows, I say "the" Windows share; while both Win98 machines have various shares, only one of them really counts. I use an extra hard drive on one of them as a sort of file server and keep all my data there,]


At the moment, Ubuntu auto-mounts the Windows share in the directory ~/.gvfs once the share is accessed. But I'd rather have this auto-mounted into a more sensibly named directory, and done automatically at boot up.

I've been following the directions at

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

but when I try to mount the Windows share via **sudo mount -a**, I get an error message

[i]mount error: could not find target server. TCP name RAY/D-DRIVE not found
No ip address specified and hostname not found[/i]

All three machines are assigned IP addresses by a Linksys router/firewall using DHCP. I tried changing them to static IP addresses, but that caused perplexing problems I had no idea how to resolve.

Unfortunately, there are endless web pages and forum messages that touch on these matters, and when I try to find out how to sort out my problems I am confronted with TOO MUCH INFORMATION, TOO MANY OPTIONS.

[If I could attach an audio file of myself screaming at this point, I would.]

Can someone direct me to a single, reliable, comprehensive page "how to connect Ubuntu 8.04 to Windows 98 shares" that sorts out how to deal with dynamic IP addresses assigned using DHCP?

Or is this an impossibility?

Not to complain, but it's very frustrating. It's s-o-o-o-o easy to do this on Windows (and has been for 15 years); why is it so tricky w. Linux?

---

### Post by dwanders on 2008-09-13
I have had many problems with mounting Windows shares and getting samba to work correctly (or reliably) until I found steps to use the command mount.cifs I cannot seem to find the link to the instructions I found and my scripts are at work. AS soon as I find them or can get to my work scripts I will post the info to see if it helps. If I recall you just install smbfs, and then use mount.cifs - I am sure its not the most secure stuff, but it seems to work consistently enough for me to use in backups.

---

### Post by dwanders on 2008-09-13
Oh - and I truly do feel you pain, but dont kid yourself - I too have been doing this for many years, and there is nothing more frustrating than having your windows systems that have worked forever and love break because of some changes MS decided to make int the way it does things without telling anybody. Or the way they so cutely deviating from the world standards just enough to be a pain the *** for any little thing you want to do - just try and access a Win 2003 servers or participate in the 2003 domain with those old windows and you will quickly see how MS screws its own. We have actually found it is easier for our windows clients to globally access Linux shares than windows ones when you get it all going - and it is very reliable and consistent. 

Ok off my soap box - let me see if I can find those scripts or commands =)

---

### Post by dwanders on 2008-09-13
#Mount MFS share then rsync the files for changes
/sbin/mount.cifs //Server/share /mnt/net_home -o username=uname,password=password,uid=uname,gid=uname,file_mode=0640,dir_mode=0750,isocharset=u
tf8 2>&1

#Un-Mount the share
/bin/umount /mnt/net_home 2>&1

Those are the commands I use and they work every time- stilll cant find the post, but I am sure I did sudo apt-get install smbfs, then I can issue those commands. You can also use IP addresses instead of server names (if you done have WINS resolving) and I think things work better if the username is the same on the windows computer and the Linux box.

Hope this helps, if I can find the original posts or similar infor I will post it.

---

