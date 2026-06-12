---
title: "/home partition for fresh ubuntu installs"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by northwestuntu on 2009-07-19
i have a 400 gig HD.  pretty much im getting tired of moving my data off to reinstall new versions of ubuntu every 6 months.  i like doing fresh installs and not updates of ubuntu.

so would making the home folder it's own partition be a good idea so i can leave all my data there and then i can format the rest for new versions of ubuntu?  

how much room should i make for the ubuntu install?

and what's the best way to do this?

thanks

---

### Post by SuperSonic4 on 2009-07-19
Yes it would be a good thing in your case. You can use gparted to create a partition and then edit fstab to direct it to the new partition

---

### Post by earthpigg on 2009-07-19
the easiest way to do it in your case would be at the next fresh install.

select 'manually partition' -> make a 20-30 gig partition, set 'mount point' to / -> leave your swap partition be -> make the rest a partition with 'mount point' set to /home -> and ur done

---

### Post by SuperSonic4 on 2009-07-19
Perhaps but the next release will be in October which is a long time away

---

### Post by raymondh on 2009-07-19
my root (/) is 20GB.  My swap is 2GB (down from 4Gb). The rest for /home (about 350, more or less).

---

### Post by northwestuntu on 2009-07-19
> **earthpigg said:**
> the easiest way to do it in your case would be at the next fresh install.

select 'manually partition' -> make a 20-30 gig partition, set 'mount point' to / -> leave your swap partition be -> make the rest a partition with 'mount point' set to /home -> and ur done

yes i think your right in just waiting until the new version comes out to do this.  seems like it will be easier.

---

### Post by northwestuntu on 2009-07-19
> **raymondhenson said:**
> my root (/) is 20GB.  My swap is 2GB (down from 4Gb). The rest for /home (about 350, more or less).

that sounds about right for me.

---

### Post by northwestuntu on 2009-07-19
> **earthpigg said:**
> the easiest way to do it in your case would be at the next fresh install.

select 'manually partition' -> make a 20-30 gig partition, set 'mount point' to / -> leave your swap partition be -> make the rest a partition with 'mount point' set to /home -> and ur done

after the new install will my files already be waiting in my home folder? or do i need to point ubuntu to the new home folder area?

---

### Post by SuperSonic4 on 2009-07-19
Your /home folder will be blank when you've first created it but ubuntu will automatically create fstab with /home pointed to the new partition so when it's installed it will recognise it as a separate home

---

### Post by northwestuntu on 2009-07-19
> **SuperSonic4 said:**
> Your /home folder will be blank when you've first created it but ubuntu will automatically create fstab with /home pointed to the new partition so when it's installed it will recognise it as a separate home

so then after that i should be able to format the / and install new versions of ubuntu and my /home will stay untouched and ubuntu will pick it up after each new install.

---

### Post by earthpigg on 2009-07-19
> **northwestuntu said:**
> after the new install will my files already be waiting in my home folder? or do i need to point ubuntu to the new home folder area?

the *first* time, it will be blank, until you either restore your backed up /home or start installing things, bookmarking things, etc...

...but after that on 'fresh' installs, as long as you ensure you select 'no' for 'format partition', and set that partition to mount as /home, your stuff will be waiting for you.

---

### Post by northwestuntu on 2009-07-19
> **earthpigg said:**
> the *first* time, it will be blank, until you either restore your backed up /home or start installing things, bookmarking things, etc...

...but after that on 'fresh' installs, as long as you ensure you select 'no' for 'format partition', and set that partition to mount as /home, your stuff will be waiting for you.

ok gotcha.

thanks

---

### Post by SuperSonic4 on 2009-07-19
> **northwestuntu said:**
> so then after that i should be able to format the / and install new versions of ubuntu and my /home will stay untouched and ubuntu will pick it up after each new install.

Yes.

On that note it may be wise to check it once in a while and manually remove anything you don't need anymore unless you simply don't care XD

---

