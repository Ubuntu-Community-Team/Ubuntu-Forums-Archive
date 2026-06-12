---
title: "Questions about manual partitions with Ubuntu"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by shughard on 2009-10-03
I currently have 9.04 installed on my pc. My pc has a 32gb ssd drive and two 640gb hdd running raid0 with hardware raid.

I had 9.04 already installed on the raid0 when I bought the ssd drive. So I installed 9.04 ext4 on the ssd. Then I moved /tmp and /var to a tmpfs in ram. I set my raid0 to mount at boot use it for storage.

I am not happy with this current setup. From what I have been reading I could have done this better. So I am thinking about doing a clean install with a different partition scheme like this:

32gb ssd
partition 1 / 32gb ext4
1280gb raid0
partition 1 swap 10gb
partition 2 /tmp 10gb ext4
partition 3 /var 10gb ext4
partition 4 /home 1250gb ext4

I have several questions about this.

1) Do my partitions look right to maximize performance and minimize writes to the ssd?
2) Can the standard ubuntu install disk do what I am wanting to do?
3) Since my /home is mounted on the raid0 and my / mounted on the ssd will I be able to upgrade/do clean installs without losing this data and if so how do I get the new install to utilize the the /home partition on the raid0 drive as the /home partition in the new install?

Thanks

---

### Post by earthpigg on 2009-10-03
i've never worked with RAID hands-on before, but ill answer what i can,

1) yes. but, as an SSD user myself, i think the whole "minimize writes or your SSD will asplode!!" thing is overblown. my expectation is that if one makes such efforts, the SSD will fail in 5.5 years instead of 5 years. but, time will tell.

2 and 3) i suppose that would depend -- does the live CD recognize the RAID0 setup correctly?

your setup does not look very fault-tolerant at all, and looks 3x as likely to fail as something a bit more conventional - if any of the 3 drives fail, your system will fail. im sure you are already aware of that, though.

towards the end of the manual partition phase of the setup, there is an 'advanced' button... it lets you specify where to write the MBR. i would be sure to verify that it is being put on the SSD.

---

### Post by shughard on 2009-10-03
> **earthpigg said:**
> i've never worked with RAID hands-on before, but ill answer what i can,

1) yes. but, as an SSD user myself, i think the whole "minimize writes or your SSD will asplode!!" thing is overblown. my expectation is that if one makes such efforts, the SSD will fail in 5.5 years instead of 5 years. but, time will tell.

2 and 3) i suppose that would depend -- does the live CD recognize the RAID0 setup correctly?

your setup does not look very fault-tolerant at all, and looks 3x as likely to fail as something a bit more conventional - if any of the 3 drives fail, your system will fail. im sure you are already aware of that, though.

towards the end of the manual partition phase of the setup, there is an 'advanced' button... it lets you specify where to write the MBR. i would be sure to verify that it is being put on the SSD.

Thanks for your reply.
My raid setup is a true hardware raid and is transparent to the OS it sees it as one 1.2tb drive.

I am aware that my system is less fault tolerant than some. I backup all my most important files regularly so I am not worried. 

The thing that I am most concerned about is this being able to keep my home folder with all documents and files each time I do a fresh install of the os. 
When I do the fresh install how do I tell the installer to use my existing home folder without it erasing my data?

---

### Post by earthpigg on 2009-10-03
> **shughard said:**
> 
When I do the fresh install how do I tell the installer to use my existing home folder without it erasing my data?

well, first you still want to back up anything vital of course. you already said you did, but im saying it again because it makes me feel warm and fuzzy.

manual partition -> select the /home partition, tell it ***not*** to format it and to set its mountpoint to /home.

and that should be it, off the top of my head. i've done it before, but i always scrutinize the interface very carefully... there may be something i am forgetting but would know if i saw it. one of those "oh yeah, THAT! dont want to forget that..." things. sorry i can't be more specific.

---

