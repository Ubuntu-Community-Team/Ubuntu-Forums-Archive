---
title: "Siemens DVB-C Install Help"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by Wilb on 2006-03-08
How do,

Basically I've managed to get myself in a right tangle trying to get my Siemens Fujitsu DVB-C card set up within Ubuntu 5.10. My aim is to get VDR set up (ideally 1.3.44) and I've actually managed to get this properly compiled, however I can't for the life of my sort the driver for the DVB card out. 

After doing hours of searching last night, some people seemed to suggest that the DVB driver I'm after should be compiled into the default Ubuntu kernel, however if thats the case then I'll be damned if I can figure out how to get it loaded. I *think* the module name I'd be looking to load would be dvb-ttpci. I even found a file called dvb-ttpci.ko but couldnt insmod that.

I've also tried looking in the repositories and theres some driver source in there, however if you download and extract this its designed for the 2.4 kernels and we're on 2.6 Following the compile instructions pretty much ends up coming back and moaning that it can't find the correct files for 2.6. I've even tried downloading the latest CVS for the drivers but am having no luck getting these compiled either - think I need to set some symbolic links to my current source and extract the CVS somewhere specific however I'm getting a bit lost doing all this cos I dont really know what I should be pointing where and I don't wanna start guessing!

Basically I'm pretty sure I'm trying to go far deeper than I need to in this - the reason I switched my vdr box over to Ubuntu was because soemone had mentioned it was a lot easier to set up than on SuSE 9.0 (which is what I was using up until my box went mad last week.) Thought I'd give Ubuntu a go cos I love it for my desktop OS and thought it would all be pretty straightforward.

Any pointers or advice anyone? Please! 

Cheers,

Wilb.

---

