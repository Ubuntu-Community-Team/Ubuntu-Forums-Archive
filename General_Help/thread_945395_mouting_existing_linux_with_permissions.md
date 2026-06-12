---
title: "mouting existing linux with permissions"
date: 2008-10-12
forum: General Help
---

### Post by quatoria on 2008-10-12
I have searched this forum and found quite a few posts on how to mount windows partitions in linux, ntfs file systems etc.

However I have a similar problem. I have a PC with Mandriva linux, the file system is ext3 and I want to install ubuntu, partly because 2009 mandriva has destroyed my system and the Live cd won't work and various other options have left me with a destroyed system, I can't do anything.

I can get the ubuntu live CD up and want to copy off the users files so that I can install ubuntu.

However it says I don't have permissions. I have read various links from the forums that make no sense what so ever because they all relate to ntfs. And they are also written in gibberish because they make no sense what so ever. My linux knowledge is limited.

Can anyone tell me what I actually type in to get the files back?

The hard drive is sda6, ubuntu can see in live as /media/disk/lisa 

I don't want to risk installing the live cd and losing all that data and I can't eve get mandriva to work.

---

### Post by sokopok on 2008-10-12
```
sudo cp -R /media/disk/lisa/* DESTINATION
```*sudo* will give you root permissions
*cp -R* will copy all files _recursively _(except hidden files of course, check if you have hidden files in the directory with *ls -a /media/disk/lisa* , if you do you can copy them by explicitely naming them in a similar invocation of *cp*)

---

### Post by quatoria on 2008-10-12
Thankyou for the reply.

I tried what you said, I managed to get some of the files off. However the list command for showing hidden files didn't work, permission denied.

Also the cp- R command did some but not all, I know there was other directories in there that contained photo's, some uni files and stuff on her desktop etc. Which haven't come across, though her hidden thunderbird file did come out with hopefully her email in it.

And it is showing a lot of "operation not permitted" errors. When doing the tmp file.

Anyway I can get in to look at the files it hasn't copied off?

---

### Post by sokopok on 2008-10-12
Correction:
```
sudo ls -a /media/disk/lisa
```You need root permissions, so you need to use sudo

The disk you mention is probably the root disk of your old install. the cp command will not copy special files like devices and probably those are the errors you get.

the cp command will not copy symbolic links unless you specify -L ( copy -L ). Maybe this is why you dont see the fotos?


If you want to copy the entire filesystem (not just some selected files or folders it might be better to use something like rsync, which is far more intelligent than the basic cp command)

sudo rsync -av SOURCE DESTINATION
will copy everything from SOURCE to DESTINATION.
If you want to be able to visually inspect which files are being copied, pipe the command to less like so:
sudo rsync -av SOURCE DESTINATION | less

in your case, to be sure I would use the following command (it will also copy hidden files):
```
sudo rsync -av /media/disk/lisa DESTINATION | less
```

---

### Post by quatoria on 2008-10-12
The ls command got me access to the files, although there is around 60 - 70 % of the files not copying off the system. Half the files and nearly all the subdirectories, like My pictures etc. (this machines was a windows replacement and I copied all files from that  directly)

What are the commands in linux for things like *.doc or a*.*

And trying to copy files that have a space in doesn't seem to work. which means most word documents won't copy over as they are two words or more.

The two word is also a problem for my destination, as it is currently a usb plug in freecom HDD, which won't be accepted. So I am using my 8GB flash pen. Which can't accept that much space.

---

### Post by sokopok on 2008-10-12
Now I'm getting a bit confused...
Do you want to copy the whole disk, or just some selected files/folders? I think you probable just need to copy her home directory, unless she had a customized setup.

In linux *.doc is *.doc (same thing)
If you have spaces, you need to
1. quote the filename like so: "Filename with spaces.doc"
or
2. escape the space like so: Filename\ with\ spaces.doc
(1. and 2. do the same thing)

---

### Post by quatoria on 2008-10-12
Aha... cracked it, your last post with the rsync has done it.

I asked about the *.* as I would do it manually and get the files I needed. However the rsync did the whole of her home directory. 9.6 GB recovered (I didn't know how many photgraphs she had.) in around 55 minutes of stressing in case I couldn't recover the files.

So I can rest easy as I finish off loading them to my External HDD and then go about installing ubuntu over what is left of Mandriva 2009.0.

And all with the Live CD. That alone is such a useful tool.


Big thanks.  :)

---

