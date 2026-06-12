---
title: "dmraid On ICH9R"
date: 2008-11-06
forum: Hardware
---

### Post by tyeken8 on 2008-11-06
Uh, I have a "big":( problem, I wanna install ubuntu on ICH9R's Matrix RAID, but dmraid don't support it.
I want to know that whether I can do that in another way.
Eg: Hack the dmraid or simulate (is it a transitive verb? My English is not so good.) the ICH9R to ICH7R (I think that's not so much difference between them.) .
Or can I install it on a whole RAID0 array?
Or install on a non-RAID drive and try to access the RAID volume in it?

I just start to learn ubuntu (also Linux), I don't want to lose heart. So pls make it easier to understand, thx.

---

### Post by tyeken8 on 2008-11-06
Up it&#8230;&#8230;Anybody knows?

---

### Post by psusi on 2008-11-06
dmraid DOES support intel software raids.

---

### Post by tyeken8 on 2008-11-06
> **psusi said:**
> dmraid DOES support intel software raids.
The following formats are supported:

 Highpoint HPT37X/HPT45X
 **[COLOR="Red"]Intel Software RAID[/COLOR]**
 LSI Logic MegaRAID
 NVidia NForce RAID (nvraid)
 Promise FastTrack
 Silicon Image(tm) Medley(tm)
 VIA Software RAID

---

### Post by psusi on 2008-11-07
> **tyeken8 said:**
> The following formats are supported:

 Highpoint HPT37X/HPT45X
 **[COLOR="Red"]Intel Software RAID[/COLOR]**
 LSI Logic MegaRAID
 NVidia NForce RAID (nvraid)
 Promise FastTrack
 Silicon Image(tm) Medley(tm)
 VIA Software RAID

Yea, that's what I said.  You initially said it doesn't.

---

### Post by tyeken8 on 2008-11-08
> **psusi said:**
> Yea, that's what I said.  You initially said it doesn't.
Err, I initially said it doesn't, but here, "it" reffers to "ICH9R's Matrix RAID" or "ICH9R"...

---

### Post by tyeken8 on 2008-11-09
Err...

---

### Post by psusi on 2008-11-09
Same thing ;)

---

### Post by tyeken8 on 2008-11-11
> **psusi said:**
> Same thing ;)
Not...
I wanna know now is: How can I install it successfully?

---

### Post by psusi on 2008-11-11
I have heard it works fine if you use the alternate cd, but I used the live cd and just had to manually install grub at the end since the installer crashed trying to install grub automatically, which didn't work.

---

### Post by BuissonVert on 2008-11-11
Yup, you have to use the AlternateCD. It worked with no problems on my fakeRAID0 (nVidia MCP). That's a great change compared to 8.04 :)

---

### Post by tyeken8 on 2008-11-12
But can I install it by WUBI?

---

### Post by tyeken8 on 2008-11-12
> **BuissonVert said:**
> Yup, you have to use the AlternateCD. It worked with no problems on my fakeRAID0 (nVidia MCP). That's a great change compared to 8.04 :)
Err, it can work on NVIDIA RAID, but not ICH9R...

---

### Post by psusi on 2008-11-12
> **tyeken8 said:**
> Err, it can work on NVIDIA RAID, but not ICH9R...

Yes, it can.  Why do you keep saying that?

---

### Post by tyeken8 on 2008-11-12
Really can? Oh, let's try about that, thank you all.

---

### Post by tyeken8 on 2008-11-22
Yes, it can.
But there's a little bit more.
After I installed the dmraid and actived it, I goto the GParted.
It said like this:

---

### Post by psusi on 2008-11-23
There is a little more what?

---

### Post by tyeken8 on 2008-12-26
> **psusi said:**
> There is a little more what?
Nothing much now, It works well. Thanks.

---

