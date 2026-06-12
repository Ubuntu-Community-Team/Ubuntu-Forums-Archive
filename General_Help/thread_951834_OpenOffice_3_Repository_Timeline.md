---
title: "OpenOffice 3 Repository Timeline?"
date: 2008-10-18
forum: General Help
---

### Post by leehach on 2008-10-18
Does anyone have any idea when OpenOffice 3 would make it to the repositories?  I don't see anything about it being included in 8.10.  I could install myself, but prefer to use repositories when possible, so I would wait if (a) OpenOffice 3 will be included in 8.10, or (b) it would be likely to make it to the repositories soon.

Thanks,
--Lee

---

### Post by GuitarRocker2562 on 2008-10-18
It will not be in the "main" repository until you update to 9.04 (not even in development yet). However, it should be in the "backpots" repository within a month or so.

---

### Post by JunCTionS on 2008-10-23
:S 
wait...
why?
Are there any bugs or issues observed with Ooo 3 and Intrepid?
Where is this decision taken?
Is there a way to upgrade from 2.4 (not install side-by-side) without uninstalling the [k]ubuntu package?

---

### Post by _sAm_ on 2008-10-23
I believe backports for Ubuntu 8.10 already have OpenOffice 3.0([https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)).

---

### Post by jjmatt on 2008-10-28
> **_sAm_ said:**
> I believe backports for Ubuntu 8.10 already have OpenOffice 3.0([https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)).

Turns out it's not. [Ubuntu developers didn't want to include]("http://www.tectonic.co.za/?p=3447") (or endorse, for stability's sake) Open Office 3 in intrepid, whatsoever.

However, you can add the [Open Office repo]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") and install it from there at your leisure. (though they suggest waiting until intrepid is fully released...not sure how much of a big deal it is).

---

### Post by snowpine on 2008-10-28
> **leehach said:**
> Does anyone have any idea when OpenOffice 3 would make it to the repositories?  I don't see anything about it being included in 8.10.  I could install myself, but prefer to use repositories when possible, so I would wait if (a) OpenOffice 3 will be included in 8.10, or (b) it would be likely to make it to the repositories soon.

Thanks,
--Lee

Hi Lee, OO 3 will *never* be in the main repositories for Intrepid, Hardy, or any earlier version of Ubuntu, because that's not how the repositories work. :) Everybody who uses the same release of Ubuntu has the same package versions, by the design and philosophy of the developers. Check this out; it's an informative read: [http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

As mentioned, there is a "backports" repository that should include OO 3 in the not too distant future. Or you can install it right now using the instructions on the OO website. 

Hope that clears it up. Good luck!

---

### Post by jimv on 2008-11-10
> **jjmatt said:**
> Turns out it's not. [Ubuntu developers didn't want to include]("http://www.tectonic.co.za/?p=3447") (or endorse, for stability's sake) Open Office 3 in intrepid, whatsoever.


I guess they learned from putting the Firefox3 beta into Hardy.

---

### Post by Chunky Dunk on 2008-11-10
> **jimv said:**
> I guess they learned from putting the Firefox3 beta into Hardy.

My understanding about the firefox issue, is that since Hardy is going to be supported for a long time, they didn't want to standardize on the 2.x. series. Now if you run the update manager in Hardy. you get the final non beta version of it.

---

