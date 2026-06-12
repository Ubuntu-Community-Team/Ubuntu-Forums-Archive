---
title: "Widescreen Support Dell Latitude D820"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by HwyXingFrog on 2006-08-10
This was posted previously in the Dapper Development area:

[http://www.ubuntuforums.org/showthread.php?t=182319&highlight=d820]("http://www.ubuntuforums.org/showthread.php?t=182319&highlight=d820")

but I am having this issue as well,  I can't get mine to use the native resolution of 1680x1050.  I tried the xorg command mentioned previously as well with the same results.

Anyone get this to work with Dapper Drake?

It also seems that there are two different styles of D820's from Dell.  Mine is the 1680x1050 (not 1900x1200), it sounds like the 1900x1200 model is an nvidia video chip and the 1680x1050 model is an intel chip.  Correct me if I am wrong.

Thanks

---

### Post by wieman01 on 2006-08-10
Would you want to try "855resolution" / "915resolution"? Nice tool and easy to configure. Here is a reference:

[http://www.ubuntuforums.org/showthread.php?t=231203]("http://www.ubuntuforums.org/showthread.php?t=231203")

Intel chip...

---

### Post by HwyXingFrog on 2006-08-18
Well, it sounds like the extent of my issues were due to me having an external monitor plugged into the VGA port on the laptop.

I took it over to a different desk to try to fix the issue, and suddenly it was fixed.  When I went back to my desk and tried it again it wasn't working again.

So, the video card was trying to set up for the external not the internal screen.

Now all is good.

---

