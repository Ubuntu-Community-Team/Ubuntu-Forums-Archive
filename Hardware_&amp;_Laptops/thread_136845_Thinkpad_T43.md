---
title: "Thinkpad T43"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by vrode on 2006-02-26
Is anyone running ubuntu under this hardware?

Is so I like to exchange few notes mostly regarding screen resolution.

I can also reached at aptgetd [at] gmail.com



regards,
/virendra

---

### Post by Hachi on 2006-02-26
Check out this article on thinkwiki.org: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_5.10_on_a_ThinkPad_T43_%281871%29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_5.10_on_a_ThinkPad_T43_%281871%29)

It's a great site if you're the proud owner of a Thinkpad :) 

_________________________
Hachi - Thinkpad R50 owner

---

### Post by vrode on 2006-02-26
I'm running dapper on my thinkpad t43.

I can't apt-get install 855resolution, it says, it can't find the package.

Should I revert back to ubuntu 5.10?

Also, can you share your xorg.conf? I'm guessing you are running ubuntu on thinkpad t43?


regards,
/virendra

---

### Post by abhaysahai on 2006-02-26
[QUOTE=vrode]I'm running dapper on my thinkpad t43.

I can't apt-get install 855resolution, it says, it can't find the package.

Should I revert back to ubuntu 5.10?

Also, can you share your xorg.conf? I'm guessing you are running ubuntu on thinkpad t43?


regards,
/virendra[/QUOTE]

855resolution is in dapper "virtual" setion 
[http://packages.ubuntu.com/dapper/virtual/](http://packages.ubuntu.com/dapper/virtual/)

Please go through This wiki.
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

Hope this helps. 

> I'm guessing you are running ubuntu on thinkpad t43?

His signature says 
Hachi - Thinkpad R50 owner


It will be better to ask this question in Dapper instead of Breezy hardware support, you are more likely to get better answers.

---

### Post by vrode on 2006-02-26
I will try dapper forum. BTW, the only reason I went for dapper thinking it might fix the resolution.


regards,
/virendra

---

### Post by abhaysahai on 2006-02-27
[QUOTE=vrode]I will try dapper forum. BTW, the only reason I went for dapper thinking it might fix the resolution.


regards,
/virendra[/QUOTE]

Did you not find 855resolution in dapper "virtual" setion  ??
Is yes then why do you want to try in dapper forum?

---

### Post by vrode on 2006-02-28
no I didn't find "855resolution" in dapper.



regards,
/virendra

---

### Post by ranf on 2006-02-28
The package name now is `915resolution':

[http://packages.ubuntu.com/dapper/x11/915resolution](http://packages.ubuntu.com/dapper/x11/915resolution)

You need the Universe repository enabled.

---

