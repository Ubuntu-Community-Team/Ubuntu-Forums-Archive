---
title: "How to open root:root file with terminal"
date: 2008-07-12
forum: General Help
---

### Post by darkzeus85 on 2008-07-12
Ok I am just going to jump right into it. I was following instructions in a book on linux and it was talking about changing file permissions and ownerships. Well my brilliant mind thought if only owner can view it and I change the ownership to root:root then it would be secure to anyone that can't use terminal (wife). I figured that with a file only viewable by root that i could sudo in but i can not locate the command that I would use to view that file. any help would be great as with out it I would have lost some important files. thanks in advance.

DarkZeus

---

### Post by p_quarles on 2008-07-12
To view the file:
```
sudo less /path/to/file
```
To edit it:
```
sudo nano /path/to/file
```
That said, there are other ways to protect files from accounts that you don't want reading them. The usual one is to make sure the other user(s) has limited privileges.

---

### Post by jonlemur on 2008-07-12
I don't know if that's the best way to go about hiding files, but I think you could use ```
gksu nautilus
``` from a command line to run nautilus with root privileges, and that should let you view any files owned by root (and I think anyone else).  Hope that helps.

---

### Post by darkzeus85 on 2008-07-12
I only have one account and if I make another one the other user gets mad and thinks i'm hiding something so i needed to do something to keep wondering clicks from opening it.

I'm about to try your suggestion I will let you know if it works.

---

### Post by p_quarles on 2008-07-12
> **darkzeus85 said:**
> I only have one account and if I make another one the other user gets mad and thinks i'm hiding something so i needed to do something to keep wondering clicks from opening it.

I'm about to try your suggestion I will let you know if it works.
Depending on how elaborate you'd like to get, you could pretty much make an entire directory of stuff that was invisible to anyone who didn't know exactly what to look for. I.e., you could set up an encrypted container filesystem that you could mount when needed. In addition to not being obvious to less technical users, this would also be impossible to crack without the password.

Whatever works, though, of course.

---

### Post by darkzeus85 on 2008-07-12
> **jonlemur said:**
> ```
gksu nautilus
```

Thanks jonlemur Nautilus worked like a charm. 

By the way I messed up by saying it's a file it is a directory so that is why I think the 

```
sudo less /path/to/file
``` 

did not work but thanks both of you for rapid responses I wish I could get as quick of a response on other threads.

---

### Post by darkzeus85 on 2008-07-12
p_quarles how percisely would one do that?

---

### Post by p_quarles on 2008-07-12
> **darkzeus85 said:**
> By the way I messed up by saying it's a file it is a directory so that is why I think the 

```
sudo less /path/to/file
``` 

did not work 
Yeah, that's why it didn't work. "less" is a text file reader. To view a read-protected directory:
```
sudo ls -al /path/to/file
```

---

### Post by darkzeus85 on 2008-07-12
How would I make an encrypted container?

---

### Post by p_quarles on 2008-07-12
First, install a couple packages:
```
sudo apt-get install dmsetup cryptsetup
```
and enable a couple of modules:
```
sudo modprobe aes; sudo modprobe dm-crypt
```
To make sure you're set up run:
```
sudo dmsetup targets
```
which should produce something like this:
```
crypt       v1.1.0
striped     v1.0.2
linear      v1.0.1
error       v1.0.1
```
Now, create the container:
```
sudo dd if=/dev/zero of=~/secrets.img bs=1M count=100
```
Not that "secrets.img" is the name of the container file, and "100" is the number of megabytes in this container. Both of these values can be changed as needed. 

Now, make it into a loopback device:
```
sudo losetup /dev/loop0 ~/secrets.img
```
and encrypt it:
```
sudo cryptsetup -y create top-secret /dev/loop0
```
This step will ask you to create your passkey, which you will enter and then confirm. Now you just need to format this container:
```
sudo mkfs.ext3 /dev/mapper/top-secret
```
And finally, to mount the container:
```
sudo cryptsetup create top-secret /dev/loop0
sudo mount /dev/mapper/top-secret /mnt/top-secret
```
You will now be able to open the directory "/mnt/top-secret" to browse and manage files in the container. To unmount and encrypt:
```
sudo umount /mnt/top-secret
sudo cryptsetup remove top-secret
```
Like I said, this could be overkill, but it's absolutely going to keep everyone out of your files.

---

### Post by darkzeus85 on 2008-07-12
Thanks for the info, But I have a couple of questions; how do you change the container size and also (and this may sound newbieish) is there a graphical way of mounting, decrypting, and using, as well as re encrypting the container or is it best done through terminal?

---

### Post by darkzeus85 on 2008-07-12
when enabling the modules in the second command I get this error ```
WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): No such device
``` but I did the ```
sudo dmsetup targets
``` and it gives me ```
crypt            v1.5.0
striped          v1.0.2
linear           v1.0.2
error            v1.0.1

``` so am I alright because I am about to continue the process and see if it works

---

### Post by p_quarles on 2008-07-12
I've never seen that error, so I'm not really sure. As you say, though, the dmsetup command is producing the desired output, so the device mapper is working. There's no harm in going through the rest of the steps, and if something doesn't work it might provide more insight into what the error is.

To change the size of the disk, you change the "count" attribute in the dd command. In the example I gave, it's 100 megabytes.

---

### Post by darkzeus85 on 2008-07-12
Ok everything went smoothly I think until I get to the ```
sudo cryptsetup -y create top-secret /dev/loop0
```

then I get this error after entering the passphrase twice and I know I typed it correctly both times and have tried three times with the same error

```
Command failed: device-mapper: reload ioctl failed: Invalid argument
```

And Im sorry i meant how do you change the size of the container after it is made

---

### Post by p_quarles on 2008-07-13
Hmm. Not sure what to tell you. Perhaps you could try enabling each of those modules separately to at least find out which one is causing the problem:
```
sudo modprobe aes
```
and then
```
sudo modprobe dm-crypt
```
If it can be narrowed down, the solution might be easier to find.

I don't believe you can change the size of the container once it's been created. Just make a device that's large enough for your anticipated needs. It's easy, though, to create another one at any time.

---

### Post by darkzeus85 on 2008-07-13
I did as you said and the dm-crypt worked fine i guess since there was no error message after enter just a new prompt. but after the aes it gives me this error

```
WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): No such device
```

---

### Post by p_quarles on 2008-07-13
Hmm. Well, it's been some time since I've done this (I now have whole disk encryption for where I need it). In any case, I get the same error, so either A) I failed to write down a package that's needed for this to work, or B) the procedure has changed in newer versions. One thing that appears on a search of the repositories for related packages is the loop-aes-module. I'm working on Debian at the moment, so it *might* be different on Ubuntu. Still, try this:
```
sudo apt-get install loop-aes-modules-`uname -r`
```
and try again. I have a feeling that's the missing package in question.

---

