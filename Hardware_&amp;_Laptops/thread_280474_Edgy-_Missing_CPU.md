---
title: "Edgy- Missing CPU"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by benhall on 2006-10-19
Since upgrading from dapper to edgy, my core duo laptop has ceased recognising both cores (from /proc/cpuinfo). Has anyone else had this problem? It is intermittant, and I can't find a fix or any other reports

---

### Post by ciscosurfer on 2006-10-20
Seems like the 2.6.17 kernel doesn't recognize your 'duality' (sorry, couldn't resist that one.)  I believe I had this same issue.  Not sure what to tell you either.  I've thought about compiling my own kernel to make use of my hyperthreaded cpu (it's not dual cpu, but it is dual core)......there's been much talk on the forums about why the dev's decided not to support specific arch's...and the main reason what that they didn't see any real performance gains, or rather the performance gains didn't seem to outweigh the time and effort it would take them to create seperate kernels.  I am just as curious on this issue as you are.  If you hear of anything, please continue to post here.  Anyone else, please enlighten us on this very (upsetting) issue ;-(

---

### Post by benhall on 2006-10-20
Thanks for your response. I thought that there was one generic kernel too- but it seems when I upgraded it installed an different i386 kernel instead, which didn't have smp. This also booted in preference to the generic kernel which I installed later, so that is where the intermittance came from. Personally, I don't have an issue with a single kernel for all desktops, but its confusing it they don't keep to that rule.

---

### Post by mrojas73 on 2006-10-28
I just upgraded my Aspire 5601 AWLMI to edgy and it is very nice.  I had the same issue, the system booted I went to system monitor and of course it was showing just one cpu.  After reading your posts and doing a uname -r I realized that the system was using the 386 kernel so I rebooted and at the begining of the kernel uncompression I pressed ESC and selected the generic kernel.  Now the system monitor shows 2 cpus.  

I just have to learn how to setup the system to boot from the generic kernel automatically instead and I will be all set.

---

### Post by mrojas73 on 2006-10-28
Here is the solution: [http://www.ubuntuforums.org/showthread.php?t=282956&highlight=kernel+boot]("http://www.ubuntuforums.org/showthread.php?t=282956&highlight=kernel+boot")

---

### Post by neuropsychguy on 2006-10-28
When I just did the upgrade from Dapper to Edgy I had to install the generic kernel to get both processors to show up; for some reason it didn't install with the upgrade. I decided to do a clean install just to keep everything tidy and it worked right away. The solution mrojas linked to works too.

---

