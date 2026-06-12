---
title: "winMD5Sum Values"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by san65 on 2009-09-01
[SIZE=2][FONT=Verdana]Hello,

This issue is about the MD5 hash value for the ISO copies downloaded by me. The values do not match with the list of hash values available here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

The version being downloaded is: ubuntu-9.04-desktop-i386.iso. I am using winMD5Sum software to generate and compare the hash values.

The hash value of the copy downloaded through torrent is: 95e1c578b87da734ee0627b68b9e467c.

The hash value of the copy downloaded from one of the FTP servers is: 5b2488ba0fd3091e8e22a70fda2f544a.

Does this imply that there is some problem with these two copies, and that I should keep downloading the files till I get a perfect match? Each download session lasts several hours, as you know!

Thanks for your time and sharing your knowledge... much appreciated! :D
[/FONT][/SIZE]

---

### Post by presence1960 on 2009-09-01
Your iso is corrupted. Try downloading from a torrent - stay away from direct downloads. The hashes must match exactly or the iso is no good. For more info see [here]("https://help.ubuntu.com/community/HowToMD5SUM"). For hashes see [here]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by san65 on 2009-09-02
[SIZE=2][FONT=Verdana]Hi presence1960,[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]Thank you for your answer.[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]I saw just one single link of torrent on the Ubuntu website, which I have already downloaded from. Should I repeat the process?[/FONT][/SIZE]

---

### Post by presence1960 on 2009-09-02
> **san65 said:**
> [SIZE=2][FONT=Verdana]Hi presence1960,[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]Thank you for your answer.[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]I saw just one single link of torrent on the Ubuntu website, which I have already downloaded from. Should I repeat the process?[/FONT][/SIZE]
Yes, burn the iso as an image to CD-R and try installing again after using the "check disk for defects" option when you boot the CD. Report back please how it goes.

---

### Post by automaton26 on 2009-09-02
I've never had a problem with direct downloads, over ADSL, but you're right to keep trying until the MD5SUM matches exactly. Just be sure you're comparing the right one !

Also, verify your CD after burning it - there's usually an option for that in most burning software. Better to be really sure :)

---

### Post by Partyboi2 on 2009-09-02
> **san65 said:**
> [SIZE=2][FONT=Verdana]Hi presence1960,[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]Thank you for your answer.[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]I saw just one single link of torrent on the Ubuntu website, which I have already downloaded from. Should I repeat the process?[/FONT][/SIZE]
If you have download the iso using a torrent you should be able to force recheck it and it should download any missing bits.

---

### Post by san65 on 2009-09-03
[SIZE=2][FONT=Verdana]Hello,

Thank you all for your excellent advice! Really appreciate them.

I have been working to get the ISO image from diverse sites. Three downloaded so far, and one from the (only) torrent URL. All four of them fail the winMD5Sum-generated value. Before proceeding to stretch my patience with the fifth download, was wondering if there is some efficient File Transfer Manager to which I can point the download URL and which will keep downloading the file, suspend it midway whenever I want and then resume the operation at will? Something like Microsoft's File Transfer Manager? That will be a great help, if it is available.

I am supposed to have a 512kb broadband ADSL connection; which has stood me in good stead for all these years with huge file-downloads in excess of 1GB, therefore the only one to blame is me alone and not anybody else...

My first foray into Linux, and geez, the trouble has already started!
:)
[/FONT][/SIZE]

---

### Post by san65 on 2009-09-10
[SIZE=2]Hi all,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]The .iso download has worked. The WinMD5Sum value has matched.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thank you everyone for your guidance... much appreciated!:)[/SIZE]

---

