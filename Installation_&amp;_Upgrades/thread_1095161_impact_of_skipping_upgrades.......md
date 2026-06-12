---
title: "impact of skipping upgrades......"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by vrv123 on 2009-03-13
Hi experts,

Currently I am on ubuntu release 8.10 & have heavily customized my system....

What will be the consequences of directly upgrading to the next LTS release and skipping the upcoming releases 9.04 & 9.10 ?
I do not want to upgrade and disturb my stable-system for now.

Please advice.....

---

### Post by vrv123 on 2009-03-13
can anyone pls reply....

---

### Post by avtolle on 2009-03-13
By "directly upgrading", I take it you mean not doing the intermediate upgrades, then doing a complete fresh install of 10.4 (which should be LTS), as you would not be able to do a "network upgrade" from 8.10 to 10.4, based upon the history to date, which allows the network upgrade from, e.g., 7.10 to 8.04, but not, e.g., from 7.04 to 8.04.

As your system is "heavily customized" and stable, there would be no compelling reason to do the intermediate upgrades unless there were things contained in them, such as the change to ext4 fs, of which you would want to take advantage, so long as your system continues to do that which you wish.

You would, IMO, need to keep adequate records, etc., of what you did to arrive at your current state if that continues to be satisfactory so, upon the fresh install, you could recreate the same (to the extent such would be possible).

---

### Post by vrv123 on 2009-03-13
Thanks avtolle!

based on your reply, seems to me that I cannot skip the consecutive upgrades 9.04 and 9.10 to get to next LTS.
the only thing I am paranoid about is the no. of files that I have tweaked, settings made etc etc to bring the system to a stable state as it is in TODAY. I have not done any book keeping on these changes but yea I do remember most of the settings but NOT all. 

I loveeeeeeeeeeeeeeeee Ubuntu and linux but the only thing I hate about ubuntu is the 6 month release cycle. That seems to be too quick an arrival at the time when a user has just settled down with a prior release.
what do you think ?

---

### Post by Therion on 2009-03-13
Create a separate /Home partition.  

This will DRASTICALLY smooth out release transitions.

That being said, just because a new release comes out does not mean you have to upgrade to it.  If 8.04 is working for you I'd suggest sticking with it until there is some compelling reason to upgrade.

---

### Post by avtolle on 2009-03-13
My thoughts on your final point are that Ubuntu has decided to not adopt a "rolling release" form of distro; that is, to not continuously provide updated application programs, etc., throughout the term of the release, but determined to stay with the Debian model (as I understand it) that provides new and updated applications at the release points. Thus, the desire to obtain newer apps by the end users is satisfied by the frequent new version releases, rather than worry about ensuring compatibility of the same with older kernels, etc., which likely is more work for the devs to ensure stability.

As my needs are rather simple, the release every six months to get newer apps works for me; I suspect I could be happy with Debian stable, for example, but from time to time I find the need to have access to newer versions of certain applications, especially Open Office, for my work with clients. Before anyone chimes in about upgrading to OO3, I wish to point out that my production hardware is a Mac G4 Cube; short of compiling the latest OO from source, I've not found any debs for OO3 for the ppc processor. Thus, if ppc 9.04 has OO3, I'll upgrade to it when it is out in stable form to get OO3; otherwise, I'd likely stay where I'm at (8.04 LTS on my production machine; 8.10 on the testing machine, which is the same model) until a later release meeting my limited needs is out. 

It is all a matter of philosophy, isn't it? I get my systems set up where I want/need them rather quickly, so the six month cycle is not so onerous for me. I appreciate that others have different circumstances, and that the six month release cycle can prove onerous to them.

EDIT: Yes, creating a separate home partition does make the upgrades much smoother. I'd recommend you do that, if you have not previously.

---

### Post by vrv123 on 2009-03-13
Great replies Therion and Avtolle! 

Thanks much.

---

