---
title: "Cannot Use Synaptic Pakage Manager"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by rhinokh on 2009-09-05
Several days ago, I installed some package included some proxy program. Now I cannot acess my synaptic pakage manager. I tried to unistall the programs that related to proxy but still the problem existed. Another important thing is that I can open the other website but except the websites that belonged to Ubuntu ( this forum also includesd). I hope anyone here can help me!

---

### Post by akudewan on 2009-09-05
> **rhinokh said:**
> Now I cannot acess my synaptic pakage manager.

Do you get any error? If so, what does the error say?

---

### Post by Partyboi2 on 2009-09-05
Check Synaptic under Settings-> Preference -> Network that the settings are correct.

---

### Post by renge on 2009-10-02
After checking package manager one day, I unchecked a line in the section marked as (I believe) archives.  Since then, whenever I try to go into Synaptic, I get this:
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

It can't get past that.  Help, anyone?

---

### Post by diesch on 2009-10-02
There is an error in line 47 of the file  /etc/apt/sources.list. Please attache that file if you can't fix that error yourself.

---

### Post by Partyboi2 on 2009-10-03
> **renge said:**
> After checking package manager one day, I unchecked a line in the section marked as (I believe) archives.  Since then, whenever I try to go into Synaptic, I get this:
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

It can't get past that.  Help, anyone?
Open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by Cobaltx on 2009-10-05
I am a complete newbie :( I have just recently installed Ubuntu 9.04 (dual boot set up) and I used the update manager and downloaded and installed the lot.

Now I was trying to play chess in 3D and was advised I needed to install python, so I looked for help in the forums, typed in the recommended text and I get the same 'malformed line 54 in source list /etc/apt/sources.list (dist parse), E: the list of sources could not be read'

As useful as a hip pocket in a singlet to me, can someone help pls

---

### Post by Partyboi2 on 2009-10-05
> **Cobaltx said:**
> I am a complete newbie :( I have just recently installed Ubuntu 9.04 (dual boot set up) and I used the update manager and downloaded and installed the lot.

Now I was trying to play chess in 3D and was advised I needed to install python, so I looked for help in the forums, typed in the recommended text and I get the same 'malformed line 54 in source list /etc/apt/sources.list (dist parse), E: the list of sources could not be read'

As useful as a hip pocket in a singlet to me, can someone help pls
Can you provide the output to the command I posted in my previous post?

---

