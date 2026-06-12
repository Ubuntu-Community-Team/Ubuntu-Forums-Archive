---
title: "HP Photosmart C6180 [Resolved]"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by ravalox on 2006-12-29
I just got an HP Photosmart C6180 and I'm trying to get it working in edgy.  I downloaded some driver from HP, but when I run it, it hung up while trying to install dependencies, now when I rerunthe same installer it says: ```
The following packages have unmet dependencies:
  lsb-core: Depends: postfix but it is not going to be installed or
                     mail-transport-agent
  mailx: Depends: postfix but it is not going to be installed or
                  mail-transport-agent
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I'm trying to figure out how you install this printer in linux, any ubuntu success stories you can enlighten me with.

---

### Post by tajreed on 2006-12-29
Did u try to install via System/administration/printing? Or by getting HPLIP from the repos. Either one should install the printer easily.

---

### Post by mikeytag on 2006-12-31
I just bought a C6180 and got it working in Edgy. I was ecstatic to see that it was so easy compared to the Windows PC in my office. As I am typing this the Windows machine is chugging along with HP's CD o' crap software just to be able to be print to the darn thing. It even requires a reboot or two. Total install time with Edgy: 2 minutes - Windows: 30 minutes (no joke)

I haven't tried to install this printer via a local connection. Rather, I am taking advantage of the fact that it has a built in 802.11g adapter. so cool. I added the printer to my network, with encryption by the way, and all my computers are accessing the printer through the network.

1: Go to System>Administration>Printing and double click "New Printer"
2: Under "Printer Type" select the Network Printer radio button.
3: Important: there is a dropdown next to the Network radio button that defaults to CUPS Printer. You need to change this. The option you want to select here is HP JetDirect
4: Once you select HP JetDirect from the dropdown there will be two text boxes. The first one is labeled Host and you need to input the IP address of your printer in this box. For me, the IP address was 192.168.0.2 but yours may differ. See step 4a for how to find out the printer's ip address. The second box is labeled Port and defaults to 9100. Leave the port option alone.
[INDENT]4a: To determine the ip address of your printer do the following. On the C6180 press the Setup key. Use the arrow keys to select the Network option and click ok. Highlight the View Network Settings option and click ok. Highlight the Display Wireless Summary option and click ok. (If you are connecting the printer via ethernet you will want to elect Display Wired Summary instead). The next screen will show you what the ip address is.[/INDENT]
5: Once you have the correct IP address entered in click the Forward button.
6: In the dropdown labeled Manufacturer select HP.
7: In the selector labeled Model choose the Photosmart C6100.
8: The Driver section should say hpijs (recommended) (Suggested). Leave that as is and click the forward button.
9: Change the Name of the printer as you would like and click the Apply button.

That's it! Your C6180 should be good to go. This is a fantastic printer and I hope the install goes as smoothly for you as it did for me :)

---

### Post by goodtimetribe on 2007-04-22
Thanks! These directions worked perfectly for me! Do you have any tips for using it as a wireless scanner?

---

### Post by txfiddler on 2007-04-25
Likewise.  Thanks that worked for me as well.  Ditto on info to get the scanner to work as well.
Cheers

---

### Post by goodtimetribe on 2007-04-26
> **txfiddler said:**
> Likewise.  Thanks that worked for me as well.  Ditto on info to get the scanner to work as well.
Cheers

I was able to get it to scan wirelessly via XSane using the instructions here:
[http://ubuntuforums.org/showthread.php?p=2513118#post2513118](http://ubuntuforums.org/showthread.php?p=2513118#post2513118)

I would assume it would work for any wireless using hplip, but i might be wrong...

---

