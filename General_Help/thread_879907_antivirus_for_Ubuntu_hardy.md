---
title: "antivirus for Ubuntu hardy"
date: 2008-08-04
forum: General Help
---

### Post by ZeldaFan on 2008-08-04
What is the best antivirus/security software to use for Ubuntu Hardy? I am sharing files between Ubuntu and Windows Vista, and while I am not worried about Ubuntu, I do not want to infect windows Vista. I do not want a program like mcafee or norton that runs all the time in my background hogging up my system resources. I just need something that can scan a file for windows malware before sharing it with my windows installation.

---

### Post by perlluver on 2008-08-04
> **ZeldaFan said:**
> What is the best antivirus/security software to use for Ubuntu Hardy? I am sharing files between Ubuntu and Windows Vista, and while I am not worried about Ubuntu, I do not want to infect windows Vista. I do not want a program like mcafee or norton that runs all the time in my background hogging up my system resources. I just need something that can scan a file for windows malware before sharing it with my windows installation.

ClamAV it is in the repos.  Open synaptic and search for Clam.

---

### Post by tuxxy on 2008-08-04
I personally dont run one but you could try clamav

[http://www.clamav.net/](http://www.clamav.net/)

EDIT: To install search for clamav in synaptic

---

### Post by Ryadt on 2008-08-04
Avast is good also.
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

---

### Post by OutOfReach on 2008-08-04
[AVG Free]("http://free.avg.com/ww.download?prd=afl") has a Linux download, so does [Avast!]("http://www.avast.com/eng/download-avast-home.html"), ClamAV and ClamTK (GUI Frontend to ClamAV) (Both available in the repositories) are also good anti-virus.

---

### Post by limasierra on 2008-08-04
Clamtk is a good linux antivirus. You can install it by running "sudo apt-get install clamtk" in your terminal.

---

### Post by cybrsaylr on 2008-08-05
Just curious.

Do many people use any AV with linux?
I decided not to after reading this:

[Security in Ubuntu 8.04]("http://ubuntutip.googlepages.com/security")

---

### Post by Elfy on 2008-08-05
The thinking is that while it won't affect you there is the possibility that you have a (useless) one in Linux which you could pass on to someone using windows.

At least that is my interpretation of the many threads I have seen along similar lines.

---

### Post by cariboo on 2008-08-05
I find thunderbird does a good job of showing viruses attached to emails, I very rarely forward email so I depend on thunderbird to show me all the attachments. I've never run a virus scanner on any distribution I've run for any length of time. On the other hand all two of my windows computers run the latest available version of AVG.

Jim

---

### Post by mb_webguy on 2008-08-05
> **cybrsaylr said:**
> Just curious.

Do many people use any AV with linux?

I have AVG installed, but I've only used it once or twice.  I'm not worried at all about Ubuntu getting infected, but I have a dual boot system with Vista, and run a few programs in Wine.  

Actually, Wine was the reason I installed AVG...  I have some pretty good security apps in Vista, and rarely boot into Windows, so I'm not terribly concerned about viruses there.  But I read an article a while back about viruses running under Wine, so I decided to install and run AVG out of curiosity.

Most people I know who regularly run clamtk or other antivirus apps in Linux do it to prevent spreading viruses to Windows systems rather than out of concern for Linux getting infected.  It's especially a concern on servers that allow file uploads.

---

### Post by Vishal Agarwal on 2008-08-05
In my mail server I am using CalmAv for last 4 years. It is one giving very good result.B'cos the client machines are windows. During the last 4 year time I did hardly find 8 to 10 machines infected due to mail virus. while the machines was infected due to pen drive etc. ClamAV is available for most type of Linux Distribution.

---

