---
title: "installation issue with dual boot"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by FRGIV92 on 2008-12-05
So, a friend at school has got me wanting to try ubuntu, i am posting this from a liveCD running perfectly on my M-series gateway, i go to install in the desktop and keep going till it lets me select my installation method, some times it lets me choose if i want to do a dual boot and other it only gives me the option to delete my vista partition and go full ubuntu, i only want to dual boot at this point to try it out for a little bit

so i go and if the option to dual boot is there i give ubuntu the most possible hard drive space and vista its least possible, ive defragged my system today and shrunk the vista partition already, but when i go to continue the download from that point it freezes my laptop at 0% of the install and i need to shut it down and reboot

my question is how do i get the install to continue and able to resize the partition (what it says its doing when it freezes)

---

### Post by karamu on 2008-12-06
I have exactly the same problem as this- any help would be very much appreciated- I have installed Ubuntu plenty of times before and never had any issues.

---

### Post by FRGIV92 on 2008-12-06
I am still haveing the same issue, i have figured out how to get the choice to give vista and ubuntu two different partitions, i need to do a disk check after i turn my laptop on after it freezes during the resizeing partition phase

---

### Post by FRGIV92 on 2008-12-06
bump

---

### Post by Shwefty on 2008-12-06
First off, check out the partitioning section [here]("https://help.ubuntu.com/community/Beginners/FAQ").  There are a ton of useful links.

---

### Post by Shwefty on 2008-12-06
Okay, so you boot to the LiveCD, have you checked the CD for defects?  You *really* need to do that.  It's on the first boot up screen.

Second of all, [this link]("http://www.psychocats.net/ubuntu/partitioning") was on the page of the first link I sent you.  It's pretty good.  I wouldn't use FAT32 though.  I would just have my Windows partition be NTFS and my Ubuntu be ext3 as Ubuntu can read/write to NTFS (but not vice-versa).

---

### Post by Shwefty on 2008-12-06
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

I just found that link, it's phenomenal for this issue.

---

### Post by FRGIV92 on 2008-12-06
i did not check my cd for defects taht may be the issue, because ive tried both to seperate the aprtition opption and teh manual option and both freeze my laptop instantly

[Edit] I checked my CD and it does have 1 defect, which is probably due to the fact that it didnt tell me when i burnt my first one but my CD's are to small for Ubuntu to fit so one of my friends at school said he is gonna bring me a official CD on monday

---

### Post by Shwefty on 2008-12-06
Awesome, if you do decide to burn another CD yourself, make sure you follow the instructions [here]("https://help.ubuntu.com/community/BurningIsoHowto").  Burn at the *lowest speed possible* and check the md5sum (see link).

---

### Post by karamu on 2008-12-07
I doubt it's the CD- I have just checked mine and there are no defects.

So, I tried the alternate install CD- it ran fine until I got to installing GRUB- this failed so I can't boot into Ubuntu which is apparently installed.....

This is getting seriously frustrating- I previously had no issues installing Ubuntu!!

---

### Post by Shwefty on 2008-12-07
Hey Karamu, I'd start a new thread for help with this problem.  I don't know how to help you with that, and the people who would most likely won't read a thread with 7 or so replies...that and it is most likely different from FRGIV92.

---

### Post by falcon61102 on 2008-12-07
karamu,

If you do start up a new thread for this issue, post a link here so those following this thread will have an idea where to go.

And to help you with your GRUB issue try booting up from the LiveCd and running the following commands in the Terminal:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
Setup (hdX)
```

When you do the find command it should give you a result that looks something like (hd0,0) and you'll use that for the next two commands as shown.

If you get any errors, either start up a new thread or post here.  Otherwise let us know how that works out.

---

### Post by karamu on 2008-12-07
OK, thanks for the input- I'm in the live CD now- when I run GRUB in the terminal, this is what happens with the find command you suggested:

Error 15: File not found

Do you have any further suggestions or should  I just start a new thread? I've now tried three different ways to install Ubuntu on my new setup and every one fails!!

---

### Post by karamu on 2008-12-08
I have started a new thread for all my installation errors.

You can find it at:

[http://ubuntuforums.org/showthread.php?t=1005327](http://ubuntuforums.org/showthread.php?t=1005327)

thanks.

---

