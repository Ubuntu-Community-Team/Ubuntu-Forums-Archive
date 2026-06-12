---
title: "Gparted fails -- mystery"
date: 2008-06-24
forum: Hardware
---

### Post by Average_Joe on 2008-06-24
Hello all,

I appreciate in advance any expert opinions.

I've been dual-booting and triple-booting Windows alongside Linux distros for years.  And then along comes a real mystery,  on my own personal laptop no less.

Before I continue, I want to say right up front that the only variable which is different below from the dozens of times I have done this before ... is that the machine in question is running sp3 of XP Pro.   (and not sp2)

It's a Lenovo 3000 N100 with an 80GB drive.  It has had my own installations of (fresh) Win XP Pro and Ubuntu many times over on it!  That is why the issue described below is a real surprise.

So I decided recently to clear out the gunk, and reformat and reinstall.  As I have many times on this machine before, as well as dozens of other machines ... I did the following: Keep in mind that the application of XP sp3 is the only new thing here.

(1)  Used Win XP Pro sp2 installation CD (my legit copy) to slow format NTFS along all 80GB.
(2)  Installed XP Pro sp2 using the same CD, of course.
(3)  *newness* Used a stand-alone CD of sp3 soon after, to apply sp3 to this Windows installation.
(4)  got all drivers up and running, got MS updates, etc yada yada usual Windows stuff

Now at this point, what I would normally do is use a stand-alone bootable CD of GParted to shrink the 80GB Windows installation down to a 60GB size.  I have done this many times before, even on this machine.

But this time ... something new ... GParted was unable to shrink the NTFS partition.  What?  It doesn't give any specific errors, it just comes back and says it can't complete the operation.  This is a shocker.  GParted is like my best friend -- it has never failed me before.

The only thing "new" here is the application of sp3.  Do you think that somehow sp3 could be responsible for this strangeness?

Now before I get slammed for having ridiculous supposition, let me say that I have (unfortunately) observed sp3 doing weird things on Lenovo machines.  {Indeed, I have a brand new Thinkpad as well, in addition the machine described above.  On this Thinkpad, you can go from new factory image of sp2 ... to applying sp3 by CD ... and guess what?  Your legacy ethernet drivers are zapped by sp3.  I have confirmed this with knowledgeable Lenovo staff, and it is repeatable ... so sp3 can do weird things.}

I appreciate anyone's opinion -- and thanks!

---

