---
title: "Help - L412 + Ubuntu"
date: 2010-10-25
forum: Hardware
---

### Post by M0ru on 2010-10-25
First off, I'm new to Ubuntu and have gotten it installed by an acquaintance in straight off the DVD (he didn't even partition :/ )  

 The device: ThinkPad L412; Intel Dual Core P6000 2x1,86 GHz; 500 GB (7200 rpm); 1 x 4 GB DDR3; graphics: Intel 4500MHD; battery 6x


There are some things, I hope you could help me along with:

1.) I want to repartition the system (ideally without reinstalling it) to hold a OS partition (so i don't lose data when reseting the system), a swap (for hibernating and paging?) and a data/software partition. In relation: how much does encryption slow the system? Would it be wiser to split software and data, only encrypting the latter?  

2.)The L412 features a middle mouse button above the touchpad, but I haven't yet managed, to get it to allow scrolling. (Though all other mmb-functions work) Could it be that the Ubuntus Window Manager lacks that feature?  

3.) The L412 should be able to use Multitouch-zoom, but I don't know where to look for the right drivers, respectively how to get it running  

4.) The AudioOut interface doesn't work. Do I need to manually switch from the loudspeakers to it? If so: how?  

5.) How do I configure the fingerprint reader?  

6.) Does it the full 4GB RAM by default or do I have to configure something for that?  

7.) Are there any advisable powermanagment-tools? 


Already many thanks for your answers! 


greetz,
M0ru  PS: Here a Link to the retailers homepage [http://www.ubook.at/hardware/modelle-lenovo/details-lenovo/#maxi](http://www.ubook.at/hardware/modelle-lenovo/details-lenovo/#maxi) (budget model)

---

### Post by juicyoner on 2011-01-14
I'd like to bump this, as I have the exact same laptop.

---

### Post by grey.skylark on 2011-02-23
Bumping this thread as I'm seriously considering a Thinkpad L412 and would like to know the full range of issues involved in running Ubuntu on it.

Thanks!

---

### Post by gus.ke on 2011-02-23
Hey, all.  In response to the original question about re-partitioning, you will have to install again.  If you're new to Ubuntu, you should remember that if you partition manually, you will need to create an ext4 partition with the mount point "/" _**and**_ a swap partition (usually around 1-4 gigs, depending how much RAM you have).  

I have come across a blog entry that helps with the Thinkpad center-button scrolling.  I don't know if it is universal, but it worked for my 8-year-old R40.  [You can find it here.]("http://www.eastwoodzhao.com/thinkpad-middle-button-scroll-ubuntu-linux-10-04-lucid-lynx/")

I can't really help you with the other questions, but I wish you the best of luck!

-Gus in Germany

Afterthought:  Googling lead me to [this page]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader") to fix the fingerprint reader.  Looks complicated, but sometimes you have to work hard to get compatibility in Ubuntu.

---

