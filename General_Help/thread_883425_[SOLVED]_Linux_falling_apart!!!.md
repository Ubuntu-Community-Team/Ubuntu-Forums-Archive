---
title: "[SOLVED] Linux falling apart!!!"
date: 2008-08-07
forum: General Help
---

### Post by Bbman90 on 2008-08-07
I was trying to download a file in Linux, a relatively small one in fact, and I got this error message:

There is not enough room on the disk to save ***filename***.zip.part. Remove unnecessary files from the disk and try again, or try saving in a different location. 

I tried two more files on other sites with the same results. I went to the /tmp directory and saw that it said 0 bytes were free. First of all, why did that happen? I have plenty of room left on my root partition. I deleted every file in there after reading and making sure it was merely an internet cache. However, I tried to run Nautilus shortly after and it claimed it was missing configuration options. The same thing happened with Gedit. I was running firefox then, and haven't closed it for fear it may not open. I'm also not rebooting because, again, I'm afraid it won't boot. What happened? Can I fix it?

UPDATE:

I tried removing the flash plugins from the terminal to fix another problem. It said in the output something to the effect of cat: write-failed error. I couldn't delete them. I got an application crash report at the top of the screen. I hit the icon to look at it. When prompted for my password, I entered it. It was rejected. I tried it 3 times. I know I typed it in right. What is going on?

---

### Post by ibutho on 2008-08-07
If you are positive that you have only deleted stuff from /tmp, then restarting should not be a problem. Check the free disk space using "df -h" and post it back. From what you describe it seems like you have may run out of disk space.

---

### Post by Bbman90 on 2008-08-07
root@brandon-desktop:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.9G  3.9G  715M  85% /
varrun                252M  116K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   68K  251M   1% /proc/bus/usb
udev                  252M   68K  251M   1% /dev
devshm                252M   84K  251M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6             3.9G  2.8G  911M  76% /home
/dev/sda1              55M  7.2M   48M  14% /media/sda1
/dev/sda2              62G   38G   24G  62% /media/sda2
overflow              1.0M  1.0M     0 100% /tmp
/dev/sdb1             150G   51G   99G  35% /media/OneTouch4 Mini

The last one is my portable hard drive. I see that overflow, but I already deleted the /tmp files... Also, please reread first post. There is an update.

---

### Post by Mister.Vash on 2008-08-08
That overflow where /tmp is mounted looks to be the issue

The script that sets this on startup is /etc/init.d/mountoverflowtmp
it checks the available disk free space on /tmp and if it doesn't get a number greater than 0, it will create and setup overflow /tmp

Since you mentioned that you didn't want to reboot again --  I'll preface this with the nugget that I'm not sure how safe this.  I would recommend closing out any running applications, save project work, etc before doing this -- try the following:

the /etc/init.d/mountoverflowtmp file lists Usage: "mountoverflowtmp [start|stop]"

so running the following:
```
sudo /etc/init.d/mountoverflowtmp stop
```
which should unmount the overflow /tmp

after that, run the df -h to check and see if overflow stills shows - if it doesn't, check for a /tmp folder and that the permissions are correct
```
ls -ld /tmp
```
should result in something like the following with these highlightest permissions
**drwxrwxrwt** 15 **root root** 4096 2008-08-07 20:34 /tmp

If that looks different, or doesn't exist, post what it is

if that looks good, then we should probably see if the script is doing to do it again.  run:
```
sudo /etc/init.d/mountoverflowtmp
```
and then see if overflow /tmp shows up via df -h

if it doesn't, you should probably be good to go for a reboot
if it does, we may need to set -x in the script to see what information it is getting

---

### Post by Bbman90 on 2008-08-08
Thank you! I'm not sure why everything was freaking out, but this fixed it. My password even works again. However, I have a couple of questions. 1: Can I change the amount my tmp holder can change to a larger amount? Also, while your output was:
drwxrwxrwt 15 root root 4096 2008-08-07 20:34 /tmp
mine was:
drwxrwxrwt 20 root root 4096 2008-08-08 01:35 /tmp
There is only that small 15/20 difference. What does that mean?

---

### Post by Mister.Vash on 2008-08-08
My guess is that it set it on boot, maybe it couldn't read the folder or it was full.  I would just suggest checking it after reboots for a while to see if it was a one-off or if it keeps doing it.   If it keeps happening, then we may need to see exactly why it does occur when you do have free space available.

As for the 15 versus 20 - that's basically a link/file count.  It means that you have more folders/files directly under your /tmp folder than I do so it can be ignored.  Mainly what I was looking for was the permissions and the owner

---

