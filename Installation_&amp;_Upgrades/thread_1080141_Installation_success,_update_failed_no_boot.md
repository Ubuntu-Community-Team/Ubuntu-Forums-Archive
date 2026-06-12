---
title: "Installation success, update failed no boot"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by tbobker on 2009-02-25
I installed Ubuntu desktop and all went well.

The system told me i had updates, there were over 200 so i started update manager. Once this was complete, the update icon now had awarning sign. When i hovered over it a message mentions that there was a problem with update and usually this is because some updates have got unmet dependancies.

I restarted the computer and now it doesnt boot up and i get a message "Error 25".

Any advice appreciated.

Thanks.

---

### Post by sms0611 on 2009-02-25
I have a similar problem, so I thought I would post it here rather than a new thread.

I have just installed 8.04 onto a clean machine (PowerMac G4) and have been told there are 249 updates.

When I click install updates the machine hangs, or at least appears to, I left it running for 5 hours and nothing happened.

Any Ideas ?

---

### Post by Panhead Bill on 2009-02-25
Similar problem here.  Mythbuntu 8.10 install proceeds well, gives error on one package.  I used synaptic to get it and the two other files.

  Next the update manager indicates two security packages but can only download one of them.  I checked for updates and now have 168 packages to download.  At 62 of 168 packages on the progres bar, 71 packages are done, 58 failed, 10 are queued.

  I tried this yesterday and got to 138 of 168 when it stalled on 29% of one package and everything after that was failed or queued.

Any ideas?

---

### Post by cariboo on 2009-02-25
The  way to make sure you updates have completed is to open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get install -f
```

to install missing dependencies, then in the same terminal type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you can't get to the desktop, start in recovery mdoe (usually the second choice in the grub menu) and at the prompt type:

```
sudo dhclient eth0
```

substitute your ethenet device for eth0, this command will get you an ip address, then you can run the above to apt-get commands.

Jim

---

### Post by sms0611 on 2009-02-25
I have solved my problem but, unfortunately it is with the most time costly method

1) Turn off (uncheck) all of the suggested updates
2) Turn on a bit at a time the ones that look the most important in the list
3) Install the updates
4) Wait
5) Reboot
6) Repeat from 1 (above) until there is nothing left in the list

This has taken me the best part of today to do but at least I now have all updates inatalled and still have a working OS.

---

### Post by tbobker on 2009-02-25
HI jim. I cant get into the desktop because it says Error 25.

Grub does not give me any options when loading up?

By the way i use an network cable so should i leave "eth0" in your command "sudo dhclient eth0" if i manage to get to that stage.

Thanks for the help.

---

### Post by jimmyhacker on 2009-02-25
dudez i just wanna to say sudo apt-get -f install doesn`t solve anything and make things worse.i.e if python-2.6 for Macbook doesn`t exists in repository or its renamed then your update get screwed up.if update manager erased your old packages then you must 
boot live cd put your important files into flash or external disk then reinstall system.

---

