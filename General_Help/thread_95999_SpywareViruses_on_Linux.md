---
title: "Spyware/Viruses on Linux"
date: 2005-11-27
forum: General Help
---

### Post by etlatino on 2005-11-27
I have been told that there is no spyware on linux?, is this true?
  I have also been told that microsoft virsus don't affect linux users is that true?

  Do linux users need antivirus software and firewalls to protect them from the dangers of the internet and etc?

---

### Post by chajuram on 2005-11-27
Yes, you are right. No problem with anything. The scripts are written for each OS separately, so a windows spyware, virus, trojan, adware will not work in linux/mac. 

This article might help you understand the situation.

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by super on 2005-11-27
[read this post]("http://www.ubuntuforums.org/showthread.php?t=89131") it gives some information on viruses.

as to spyware, it is still a good idea to have a firewall for protection. just in case. ;)

EDIT: @chajuram - we link the same article. i guess great mind *do* think a like.

---

### Post by aysiu on 2005-11-27
Or read this:
[http://www.ubuntuforums.org/showthread.php?t=45168](http://www.ubuntuforums.org/showthread.php?t=45168)

---

### Post by Qrk on 2005-11-27
There was just a story about a linux virus a few weeks ago. If I remember correctly it required an out of date version of a fairly obscure package (on the desktop, it was a server program) and for that progam to be run as root.

If that made the news; I think Linux is very very safe.

---

### Post by shane2peru on 2005-11-27
I too was concerned about Linux firewall, so I checked my system here:  [http://scan.sygatetech.com/](http://scan.sygatetech.com/)   I tried the Symantec one too, but it didn't work with Linux.  This sygate one worked well, and convinced me that I was safe with Linux!  I use Norton with Windows.

Shane

---

### Post by soulestream on 2005-11-28
I always said on linux you don't have to worry about getting a virus with an updated system. Then one night on IRC someone said

"I just downloaded the DOOM3 RPM from Kazaa and it said I need to be root to install - how do I do that?"

Hopefully those using linux who are new to the OS learn why thats bad, quickly


soule

---

### Post by bugi on 2005-11-28
[QUOTE=soulestream]I always said on linux you don't have to worry about getting a virus with an updated system. Then one night on IRC someone said

"I just downloaded the DOOM3 RPM from Kazaa and it said I need to be root to install - how do I do that?"

Hopefully those using linux who are new to the OS learn why thats bad, quickly


soule[/QUOTE]

This is really big problem as i noticed that most of the newbies don't download distibutions from official servers, but they are using p2p for it like Kazaa etc. I'm  sure that these ISO's from Kazaa can't be 100% safe to use. Cracked software is very, very unsafe.
There was noticeably issue few months ago in my country. Some kids had downloaded cracked game from p2p and that game included virus/trojan/whatever which stole their parents credit card important data (and they lost some money). 

Imo there should be information on the official site like : do not download ubuntu from untrusted sources, download ubuntu only from listed mirrors below, or order it via "shipit" site.

Things like malware/spyware are included in closed/proprietary software, so there will be no problem with it as fas as we download packages from trusted repos :-)

---

### Post by linbetwin on 2005-11-28
What about rootkits? From what I read in [Wikipedia]("http://en.wikipedia.org/wiki/Rootkit"), those are certainly the sneakiest, most elusive pieces fo malware out there. They seem to have originated in UNIX systems as a "kit" to gain root access. They're very difficult to detect and if you do detect one it makes more sense reinstalling the OS than spending a lot of time removing the rootkit.

Is there any cause for concern for a user running Ubuntu (and Linux in general) as desktop, not server? Apart from installing packages only from trusted sources, are there any other precautionary measures we should be taking?

I know you don't need antivirus software in Linux because I have been using Ubuntu for many months and not even once have I had a problem with viruses/trojans/spyware, but those rootkits have really got me thinking.

---

### Post by bugi on 2005-11-28
[QUOTE=linbetwin]What about rootkits? From what I read in [Wikipedia]("http://en.wikipedia.org/wiki/Rootkit"), those are certainly the sneakiest, most elusive pieces fo malware out there. They seem to have originated in UNIX systems as a "kit" to gain root access. They're very difficult to detect and if you do detect one it makes more sense reinstalling the OS than spending a lot of time removing the rootkit.[/QUOTE]

Rootkits are also in Windows and they are installing there very easy, just read about Sony rootkit ;-) 

If you want to feel safe : use good/strong password for your user, make regular updates via ubuntu update, don't open ports if you don't know how to secure them, and generally this is all you need to know ;-) And you don't have to be so worry about your desktop, if you want to use Ubuntu on server then you have to know more about security but for desktop default settings (closed ports) and regular updates is imo enough :-)

---

### Post by aysiu on 2005-11-28
[QUOTE=bugi]
If you want to feel safe : use good/strong password for your user, make regular updates via ubuntu update, don't open ports if you don't know how to secure them, and generally this is all you need to know ;-)[/QUOTE] I would add:

1. Make regular backups of your documents on something external (hard drive, web server)
2. Do not keep copies of confidential information on your computer (social security number, birth date, etc.)
3. Use separate passwords for important stuff (credit card website, bank, student loans) and unimportant stuff (Ubuntu Forums... sure, it's important, but you know what I mean!)

---

### Post by anil_robo on 2005-12-03
Symantec [website]("http://service1.symantec.com/SUPPORT/ent-security.nsf/6fffc7260966992188256bf300818635/36c866e6658d455988256c380082948e?OpenDocument&src=bar_sch_nam") says there are "hundreds" of viruses for linux, and their number is growing!

---

### Post by soulestream on 2005-12-03
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)


thought that was a good read

soule

---

### Post by Galoot on 2005-12-03
[QUOTE=anil_robo]Symantec says there are "hundreds" of viruses for linux, and their number is growing![/QUOTE]
1. They're in the business of alarming people so they can sell them something. If they said that Linux was perfectly safe, more people might switch away from Windows, Symantec's gravy-train OS.

2. From what I understand, these viruses are lab-created and haven't appeared in the wild.

3. If one did appear in the wild it might effect my computer with its specific configuration and hardware and such--*if I jumped through hoops to save it, grant it executable privileges, and specifically allow it to run while I was logged on as root*--but it would be unlikely as heck to run on your computer with *its* specific configuration and hardware even if you were determined to jump through the same hoops.

4. Because of point #1 above, they don't mention points 2 and 3.

---

