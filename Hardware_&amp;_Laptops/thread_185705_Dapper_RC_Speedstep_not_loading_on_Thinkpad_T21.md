---
title: "Dapper RC: Speedstep not loading on Thinkpad T21"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by bigzak on 2006-06-01
Hi all,

I installed the Dapper RC last night because my lappy went kaput so I thought "Why wait?" and bit the bullet. VERY impressed so far. Better than I expected, which is saying something!

Anyway, I have a problem with speedstep. The Thinkpad T* series needs the speedstep-smi module loaded, and the previous install that I just blew away (Slack 10.2, linux 2.6.15) worked like a charm. However in Dapper the speedstep-smi module won't load, claiming that the device in not present.

Has anyone else had thinkpad related joy with Dapper yet?

Ta,

-- 
BZ

---

### Post by meat on 2006-06-01
> Has anyone else had thinkpad related joy with Dapper yet?

I had Dapper installed on my Thinkpad T21.  I never could get wireless to work and I had some video driver issues, but I did not have the speedstep issue.

---

### Post by bigzak on 2006-06-02
[QUOTE=meat]I had Dapper installed on my Thinkpad T21.  I never could get wireless to work and I had some video driver issues, but I did not have the speedstep issue.[/QUOTE]

Oddly enough, I have had no wireless issues at all. I did have to disable DRI otherwise I ended up with just a black screen, but strangely that only occurred a couple of days after the install.

I'm thinking of rejigging the install anyway (hey, it only takes 15 minutes :)) just in case I messed something up during ACPI selection.

---

### Post by bigzak on 2006-06-03
Right, the problem with speedstep-smi is a known bug. There is a workaround available, and a patch will be available ... shortly.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35044](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35044)

The DRI thing cropped up when I updated to the latest and greatest X.org the day of release (I was running an RC before that).

---

### Post by jimrz on 2006-06-06
[QUOTE=bigzak]
Has anyone else had thinkpad related joy with Dapper yet?
BZ[/QUOTE]

Did a clean install of dapper rc on 6/3/06 on thinlpad T42 (Pm 1.8 G + a/b/g wifi + ATI Radeon 9600). Have had none of the issues mentioned. Nearly everything worked "out of the box" with only a little minor tweaking involved. Only (non)issues are that (1) hibernate is more hit than miss (2) Conextant s/w modem. However, I almost never use hibernate (and suspend, which I do use a lot, works correctly) and  I'm pretty sure that the only time I ever used the modem was back when I first got the box just to test if I could send a fax, these are not really issues for me. The box is running so beautifully I didn't even bother to upgrade from rc (just keeping the updates current,which I am given to beleive amounts to the same as the official release).

---

