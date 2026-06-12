---
title: "command to mount a drive on boot"
date: 2013-04-15
forum: Hardware
---

### Post by breezypt on 2013-04-15
I have my Ubunto 12.10 on a seperate 500 gib drive, I have another drive that is 500 gib also hooked up. I want to use back up in the ubuntu preferences but I can't do anything to the other drive, it says I don't have permissions. I would like for it to mount on bootup, and stay up for the backup to run.

So I have 2 problems how to get permissions to even put a folder onto the spare drive, and the CLI commands to have it mounted on bootup...

Thanks,

john

---

### Post by ahallubuntu on 2013-04-15
~

---

### Post by breezypt on 2013-04-15
Thank you for responding. The mounting part I'll get, but the drive will not let me create a folder now when I manually mount it. Thats why I figured if I can gain permissions or ownerships of the drive it will let me create a folder. Right now the only folder in it is called lost and found. I want to creat a folder in media/ and name it home and just back up my home directory, this way if anything goes wrong I can just replace my home folder with a new install.

Perhaps I need to reformat it in a certain type of file system? Do you know if thats the case. I never came across a problem where a hard drive internally connected will not let me touch it, mount it or create a folder in it...

The boot part I'll figure out on google, I could really use the help with this permission/ownership problem though.

Thanks for taking the time to help.

John

---

### Post by ahallubuntu on 2013-04-15
~

---

### Post by breezypt on 2013-04-15
Ok, I'll give it a try. Can't hurt. If nothing else at least I can eliminate it as a solution if it don't work.

Thanks..

---

### Post by breezypt on 2013-04-15
Just tried to chown the only folder in the drive and it won't let me it returns this error: chown: invalid group: `johnb:lost+found' Plus it will not let me create any other folders on the drive. I have parted magic I downloaded, do you think maybe if I zero out the drive and repartition it, it may help? What file format would you use?

---

### Post by ahallubuntu on 2013-04-15
~

---

