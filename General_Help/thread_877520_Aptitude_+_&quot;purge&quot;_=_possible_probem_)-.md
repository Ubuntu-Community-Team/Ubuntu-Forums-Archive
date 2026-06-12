---
title: "Aptitude + &quot;purge&quot; = possible probem )-:"
date: 2008-08-01
forum: General Help
---

### Post by Steven45 on 2008-08-01
Hi people

I just download Hardy about a week ago and after installing it on both my room mate's computer (as well as my own), I have to say we are both very happy with it so far.

Anyway, my concern has to do with something (perhaps stupid) I did earlier using a tool called "Aptitude". I loaded it up and began checking it out a little bit. At some point, I clicked on the "purge" menu item and my machine began cooking away until I received a message warning me that I was about to delete a very important library. Under the warning, there was some garbled text and under that, there was some more text that was hidden by another screen.

Needless to say, I became quite alarmed that I had just "purged" a big chunk of something I should not have purged and yet I had expected a prompt of some type to at least warn me that I was about to purge important files but there wasn't any...it just started cooking away.

Everything still works fine but just in case I've damaged or deleted any important libraries, packages, config files, etc, is there some apt command I can use to check that my system is still in good shape and possibly make repairs in the event that something is wrong?.

Thanks again for any help, Steve

---

### Post by dark_phantom on 2008-08-01
I believe you can run "sudo apt-get check" to find out what sort of missing dependencies you have.  If so, then you can run "sudo apt-get clean" to get it fix.

---

### Post by Steven45 on 2008-08-01
I ran the ones you mentioned plus a few others and everything seems to be fine.

Thanks again

---

