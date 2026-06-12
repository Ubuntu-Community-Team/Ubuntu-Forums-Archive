---
title: "Proper File Permissions for /usr/bin"
date: 2008-10-25
forum: General Help
---

### Post by Bugs318 on 2008-10-25
Following serious warnings from a rootkit checking program (rkhunter) that warned my /usr/bin files were executable and writable by others and should be changed, I typed sudo chmod 764 /usr/bin/ then problems began - sudo lost permission to do things, certain programs wouldn't run.  Then, I logged into recovery mode and typed sudo chmod 777 /usr/bin/ as I couldn't find how to set them properly.  This worked at least insofar as everything is running, but I cannot find any info on how to properly set these files so as to not leave them at 777 and open to problems.

Please help - thank you!!!!

---

### Post by Idefix82 on 2008-10-25
I think you are in trouble. The permissions are different depending on the type of file. Most files in my /usr/bin have permissions 755 but the symbolic links seem to have permission 777.
Generally, you should never temper with permissions outside your home folder. You can try to fix it by setting all permissions to 755 and then change that of the symbolic links using 'find':
```
sudo find /usr/bin -type l -exec chmod 777 '{}' \;
```

Note: I haven't tested this command so try it with some dummy testing directory first.

---

### Post by geirha on 2008-10-25
Symbolic links do not have permissions, they just happen to show up with 777 permissions when listing them. Doing chmod 777 on a symbolic link will change the permissions of the file the link points to, so do NOT do that!

Do you know how the files got permission 777 in the first place? Did you run chmod -R 777 on something (chmod 777 is something that should be avoided at all cost, and it should never be used along with the -R option.)

Anyway, most files in /usr/bin should have 755, but some require the setuid bit set. /usr/bin/sudo is one such command, there are several others. I suggest you boot up with the ubuntu CD, mount the partition with /usr/bin to /media/disk, then run

```
sudo chmod 755 /media/disk/usr/bin/*
```
To first set all files to default permissions. Then set the permissions the files in /usr/bin/* on the CD has on your system's /usr/bin/* by pasting this in a terminal

```
find /media/disk/usr/bin -printf '%f\n'| while read file; do
  [ -e "/usr/bin/$file" ] && sudo chmod -v --reference="/usr/bin/$file" "/media/disk/usr/bin/$file" || echo "not found: $file"
done
```

The code above means: For all files in /media/disk/usr/bin/ see if the file is also in /usr/bin/ (on the CD), and if it is, change the mode of the file in /media/disk/usr/bin/ to the same as the file in /usr/bin/ .

It should revert most files to the proper modes, but not all (i.e. packages you've installed may now have improper permissions, reinstalling such packages will fix it for those packages though).

If you want to be certain of getting your system back to normal, and secure, I suggest you reinstall. Fixing this properly is hard and time consuming.

---

### Post by Idefix82 on 2008-10-25
> **geirha said:**
> Symbolic links do not have permissions, they just happen to show up with 777 permissions when listing them. Doing chmod 777 on a symbolic link will change the permissions of the file the link points to, so do NOT do that!

That's good to know, thanks!

---

### Post by Bugs318 on 2008-10-28
I am going to follow the steps outlined in a moment, but a question first: what are the other steps should I avoid the reinstall?

---

### Post by Bugs318 on 2008-10-28
Everything seems fine following the instructions - will try to reinstall most programs.  Thanks again - if there is anything else, please post, but regardless your help is appreciated!

---

### Post by geirha on 2008-10-29
Well, it depends on how files in /usr/bin got wrong permissions in the first place, was it only files in /usr/bin or may other files on your system have wrong permissions? Hard to know without knowing what command/program caused it.

---

### Post by warp4ever on 2009-08-04
Something changed by (I think) accidently tagging "use desktop as home folder" in gconf-editor / Nautilus.

Now all my map icons in "/" show a "lock" and I cannot assign icons from /usr/share/icons anymore other than to view the dir as root and perform a drag and drop.

No problems with the systemflow though, everything works fine.

BTW all permissions seem to be right :
drwxr-xr-x   27 root  root   4096 2009-08-04 23:28 icons

I have a very bad experience with changing /usr permissions so now I would not touch it with a bargepole :D

---

### Post by adedip on 2009-09-15
hi there.. I got through this..but seems I can't find a way out.. :S

Is there a way to change chmod without the sudo command in the console?

because if I don't change sudo permission I can't use sudo to change permission... :confused:

so how can I solve this?

---

