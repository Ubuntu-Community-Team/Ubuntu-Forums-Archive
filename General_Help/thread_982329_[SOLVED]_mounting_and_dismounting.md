---
title: "[SOLVED] mounting and dismounting"
date: 2008-11-14
forum: General Help
---

### Post by Bigneil on 2008-11-14
I minced my XP this morning. I never had the disc.... so remembering i still had my old fiesty disc i decided to install it, I muddled through, following the on-screen instructions. i managed to get everything working but then when Update manager asked me if i wanted to uprade from fiesty to most recent distrobution i clicked yes and let it do its thing.  BUT >>>>   once it was finnished i found i clould no longer mount one of my disk drives.  

I read the error message which suggested that i use a windows system to dismount the drive properly before retrying it. but the complication is that the drive is installed inside as a slave. i use it to store media. so, my options appear to be to remove it, install it into a case for an external (i have one) then take to a windows computer and dismount it properly. then reverse the process. or to type something clever into the terminal, i tried the phrase suggested in the error box, but the terminal replied something about only available from root.  

Thankyou for reading my post.    Any suggestions????

---

### Post by taurus on 2008-11-14
You can use the force option to mount your ntfs.  Can you post the output of this command from a terminal?

```
sudo fdisk -l
```
And since you only use that ntfs drive for storage, why not convert it to ext3?  It's much better.

---

### Post by Bigneil on 2008-11-14
Ta, so i type sudo fdisk -l into the terminal and it will force it to mount

---

### Post by taurus on 2008-11-14
No, I just want to see which partition/drive is your ntfs.  But if you know which one it is, you can try to mount it with

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/XXXX /media/windows -o force
df -h
```
Replace the /dev/XXXX with the actual device, something like /dev/sdb1 or whatever.

---

### Post by Bigneil on 2008-11-14
AWW NUTS, still nothing. 

heres a screen shot

[ATTACH]92650[/ATTACH]

---

### Post by taurus on 2008-11-14
What exactly did you run from a terminal?

---

### Post by Bigneil on 2008-11-14
ok, i think i'm making some sense now,  i think the device is called hdb1? I'll have another go and report back:popcorn:

---

### Post by Bigneil on 2008-11-14
Ace!!   (sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/hdb1 /media/windows -o force
df -h)    


That did the trick.  now will i have to force it to mount every time i want to use it, or is that it?

---

### Post by taurus on 2008-11-14
Yes, you have to use the force option each time you want to mount it and just so you know, you need to fix that problem or eventually, force option won't be able to mount it anymore.  So, back up your files from /dev/hdb1 while you still have a chance.

---

### Post by Bigneil on 2008-11-15
> **taurus said:**
> Yes, you have to use the force option each time you want to mount it and just so you know, you need to fix that problem or eventually, force option won't be able to mount it anymore.  So, back up your files from /dev/hdb1 while you still have a chance.

Thanks to you all for your guidance.

OK, that sounds a bit scary.It is now able to mount when i ask it to. no force needed. are you sure about having to back it all up?  how about i back it all up. then re-format it to something that is more Ubuntu friendly then transfer it back again. could be a real time consumer, there is around 150 GIG on it.   :(

What is ext3 ?

---

### Post by Bigneil on 2008-11-15
AW NUTS, i have a new challenge.:rolleyes:   I used a small external drive to back up some some of the files.  it also wouldn't mount, so i followed the same steps and got it working. but it refuses to unmount now. i don't want to just unplug it incase i  damage it.  the originals files are still on the   internal disk8). is there a formatting tool?     maybe i could start over.

---

### Post by taurus on 2008-11-15
How did you try to unmount it and what was the error message?  Make sure you are not in the directory that your external harddrive is before you try to unmount it.

What's the output of this command from a terminal then?

```
df -h
```

---

### Post by Bigneil on 2008-11-15
i Have managed to remove it.  I noticed that there was a folder in it that i didn't put there. (System volume information) i cut it and pasted it on the desk top and found that it would unmount and mount quite happily.  i don't know if this was a proper solution. it may not mount on the next pc i plug it into..

Thankyou for your response    

Bigneil

---

### Post by Bigneil on 2008-11-18
I have re-installed my ubuntu, Heron this time.  i have had absolutely no issues mounting or dismounting any drives at all. does this mean that my internal drive with all the media on it is safe and will continue to mount and unmount without any issues that can a rise from forcing it all the time??

---

