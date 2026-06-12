---
title: "DVD / CD drive not recognized by 10.10"
date: 2011-01-05
forum: Hardware
---

### Post by roman5x3 on 2011-01-05
I am running 10.10 and have rc1 of kde 4.6 installed. That being said I went to use my optical drive for the first time since install and it is not being recognised by kde. I insert a blank dvd that has worked in the past and I get nothing in k3b or as a pop up from kde. As for dmesg here is the output of dmesg |grep sr0:
```

[    1.149675] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.149777] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1318.246462] sr0: Hmm, seems the drive doesn't support multisession CD's

```
Please ask if you need any other info.
Roman

BTW I am familiar w/ linux (gentoo) but still a bit new to kubuntu / ubuntu.

---

### Post by wilee-nilee on 2011-01-05
Have you checked if it will play anything?

---

### Post by roman5x3 on 2011-01-05
It did recognise a dvd with a regular movie on it (not something I burned). But even with this inserted in the drive k3b is still finding nothing. I also inserted a burned dvd and it is not being recognised by kde at all.
Roman

---

### Post by wilee-nilee on 2011-01-05
That is helpful information for people who know Kubuntu, I have never used it myself. Somebody will probably post something.

Do you know how to run the apt-get in Kubuntu?

---

### Post by roman5x3 on 2011-01-05
Yes but it tend to use aptitude on the command line and lately I have been using the gui that comes built into the settings for kde.
Thanx for the help,
Roman

---

### Post by wilee-nilee on 2011-01-05
> **roman5x3 said:**
> Yes but it tend to use aptitude on the command line and lately I have been using the gui that comes built into the settings for kde.
Thanx for the help,
Roman

Personally I only use gnomebaker by and large. If you aptitude install it you will at least have a comparative cd/dvd writer. 

Not sure if gnomebaker will bring some dependencies with it, but run in aptitude you can purge it.

There are a whole lot of variables here, you may be missing some k3b plugin who knows really. You can try another writer an see if it works, you can wait for a answer. I rarely see problems with this writer, but you could purge and reinstall it just be careful it isn't removing like the whole desktop with it.

---

### Post by Balthazar_Droid on 2011-02-06
Did you get this figured out? I am having the same issue. Didn't notice it until I went to burn a DVD. I am on KDE 4.6 and Kubuntu 10.10.

---

### Post by roman5x3 on 2011-02-07
@ Balthazar_Droid 
No I have not. I got sidetracked and have not gotten back to it till now. I am currently in the middle of an update. My next coarse of action is going to be to install gnomebaker and see if it recognises the drive and if it does then I know it is k3b and not something system deep. I will post my results here when I have them.
Roman

---

### Post by Balthazar_Droid on 2011-02-08
> **roman5x3 said:**
> @ Balthazar_Droid 
No I have not. I got sidetracked and have not gotten back to it till now. I am currently in the middle of an update. My next coarse of action is going to be to install gnomebaker and see if it recognises the drive and if it does then I know it is k3b and not something system deep. I will post my results here when I have them.
Roman

@Roman I just fixed mine. I had been monkeying with Settings>Removable Devices and had "Only automatically mount removable media that has been manually mounted before" checked. I unchecked it turned off my external drive and turned it back on and it popped up. I don't if that will work for you, but I thought I would throw it out there. Good luck!

---

### Post by roman5x3 on 2011-02-12
Glad to hear that you got it fixed. I ran an update and it seemed to have fixed it. I still do not know what was wrong but it is seeing it again. My problem now is that it wont burn, but that is a topic for another thread.

Roman

---

