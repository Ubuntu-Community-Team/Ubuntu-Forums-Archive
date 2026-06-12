---
title: "Help applying a patch"
date: 2008-08-13
forum: General Help
---

### Post by Juhla Mokka on 2008-08-13
Hi,

I need to "apply patch" to get something working, but I do not know how to do that or what it is. Can anybody help?

I am following these instructions on [http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398) (POST #10) to get my wireless working after Hardy upgrade. It tells me to [COLOR=Indigo]Apply hardy patch - [http://www.alessiotreglia.com/wp-con...hardy.diff.txt](http://www.alessiotreglia.com/wp-con...hardy.diff.txt) [/COLOR]

So I have saved the text file on my desktop. What next?

I am running gnome, Hardy heron
Linux 2.6.22-14-generic on i686

Edit bodhi.zazen : The original thread was archived (and is ro)

---

### Post by bodhi.zazen on 2008-08-13
> **Juhla Mokka said:**
> Hi,

I need to "apply patch" to get something working, but I do not know how to do that or what it is. Can anybody help?

I am following these instructions on [http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398) (POST #10) to get my wireless working after Hardy upgrade. It tells me to [COLOR=Indigo]Apply hardy patch - [http://www.alessiotreglia.com/wp-con...hardy.diff.txt](http://www.alessiotreglia.com/wp-con...hardy.diff.txt) [/COLOR]

So I have saved the text file on my desktop. What next?

I am running gnome, Hardy heron
Linux 2.6.22-14-generic on i686

In general you are changing a file , ie patching it.

Put the patch in the same file as the one you are patching.

Then

```
patch -p0 < downloaded_patch
```[http://linux.die.net/man/1/patch](http://linux.die.net/man/1/patch)

Here is a brief "how to" for kernel patches : [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

---

### Post by Juhla Mokka on 2008-08-13
> **bodhi.zazen said:**
> In general you are changing a file , ie patching it.

Put the patch in the same file as the one you are patching.

Then

```
patch -p0 < downloaded_patch
```[http://linux.die.net/man/1/patch](http://linux.die.net/man/1/patch)

Here is a brief "how to" for kernel patches : [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

I have a folder called **r8101-1.009.00** to patch. This is the program I downloaded. I was told to patch it with a file:
patch file name is **r8101-1.007.hardy.diff.txt**. I have saved both on my desktop.

Does it matter that the file names are different? 
You said I should put the patch in the file I am patching. Does this mean that I should put the patch file in the folder I am patching? I cannot find any files with a similar name. Only the folder name is similar.
Regarding the code, do I type ```
patch -p0 < r8101-1.007.hardy.diff.txt
```? Or leave the .txt out?

I am sorry I have used Linux only for few months so many terms are still a bit vague to me :oops:

---

### Post by bodhi.zazen on 2008-08-13
```
sudo apt-get install patch

sudo patch -p0 r8101-1.009.00 < r8101-1.007.hardy.diff.txt
```

---

