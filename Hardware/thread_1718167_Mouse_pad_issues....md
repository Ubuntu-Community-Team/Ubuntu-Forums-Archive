---
title: "Mouse pad issues..."
date: 2011-03-30
forum: Hardware
---

### Post by tcdevotie on 2011-03-30
> **jnetman1 said:**
> You're much better off actually fixing the  problem with the driver, as telling the system that the touchpad is a  PS/2 mouse leaves you with zero control of the pad on the Mini 210. To  do this, download the attachment at the bottom of this post and save it  in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```The  kernel source will be a tarball that is installed in /usr/src. Extract  it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
```Note that  pressing tab will autocomplete to the version you downloaded. Once  extracted, change to the source directory and untar the patch attachment  you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```Now we'll patch the driver files,  copy the Makefile to the right place, and compile and install the new  driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```Reboot your machine, and you'll find the  touchpad works like it should. Note that this patch is based on Takashi  Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)


I tried the method above and everything installed correctly, however after I copies and pasted the second command "tar -xjvf /usr/src/linux-source" the following appeared and I couldn't go any further.  Any ideas?

```
tar (child): /usr/src/linux-source-2.6.35: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

---

