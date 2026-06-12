---
title: "[vaio cr31] long swapping after resuming from suspend"
date: 2009-05-13
forum: Hardware
---

### Post by sixmoney on 2009-05-13
I'm using ubuntu on my vaio cr31 since hoary. I tried suspending on hoary with no success. Also I did on gutsy, no success still. Now with intrepid I tried and it worked like a charm. Suspend and resume with no problem. 
The only big problem is the long time swapping the system takes when resumed. Time is longer if a lot of applications were open at suspend time... The strange thing about this is that swap looks like is never used before suspending....
What happens then? is the suspend script somehow pushing stuff in the swap space after going to suspend mode?

---

### Post by sir_nasty on 2009-05-13
I'm pulling this information based on discussions with friends not on personal discovery...

from what I understand ubuntu/linux only uses the swap file after the RAM is full.  If that's the case I'm guessing all your info is stored in ram, then when you suspend it writes it to the disk so now it's operating off your HDD instead of your ram.....  that's my hunch anyway....

---

### Post by sixmoney on 2009-05-13
This make sense, but what's the difference with hibernation then? In suspend mode the laptop is turned on and the ram is consuming power so why pulling data off of it??
It shouldnt write anything on disk since I want my system back with all my application in ram ready to go; I don't do it just for preserving application state but to be faster.
Any hint then? Or it's just the way suspend work: do an hibernation but slowly suck the power out of the battery? :)

---

### Post by sixmoney on 2009-05-14
any hint then?

---

### Post by sixmoney on 2009-05-16
solved... the problem seems to be compiz. Using metacity speeds up the system when waking up :)

---

