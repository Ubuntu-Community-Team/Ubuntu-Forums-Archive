---
title: "SB Extigy 5.1 (ALSA/ESD)"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by viralata00 on 2007-06-10
hello,

anyone can get the SB extigy to play 5.1 or at least duplicate the stereo for all speakers?

I've tried this:

#pcm.!dmix {
#   type dmix
#   ipc_key 1024
#   slave {
#       pcm {
#               type hw
#               card 1
#               device 0
#               } 
#       channels 6
#       period_size 1024
#       buffer_size 5120
#   }
#}
#pcm.!default {
#   type plug
#   slave.pcm "dmix"
#   slave.channels 6
#   route_policy duplicate
#}

with no success...the result was the front speaker ith a lot of noise...no duplication...

---

