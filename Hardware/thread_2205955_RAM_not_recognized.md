---
title: "RAM not recognized"
date: 2014-02-16
forum: Hardware
---

### Post by novice_penguin on 2014-02-16
Hello, I have just finished installing 4GB of new RAM into my desktop, max capacity is 4GB.  When I run the free command with -m as my argument this is what I get:
free -m
             total       used       free     shared    buffers     cached
Mem:          3150       1231       1919          0         69        548
-/+ buffers/cache:        613       2537
Swap:         2940          0       2940


My question is why does it not recognize the full 4GB?  Could this mean that one of the cards isn't seated properly?  Does this have something to do with the cache?  Thanks for any help with this matter.

---

### Post by varunendra on 2014-02-16
Please always use '**Code**' tags for posting command outputs to preserve their formatting, thus making it more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

The amount you got in MB (3150) is the "Usable" amount of memory you have. The part that seems to be not recognized may have been shared by Video buffer (the onboard graphic adapters share the memory from the RAM module to buffer the video).

Besides, if you are using a 32 bit OS, it will 'Practically' see only about 3.5 GB of total RAM. Of which, some would be taken away by the video buffer.

To see the 'Detected' memory capacity, use either of these commands -
```
sudo lshw -C memory
```
Or, for more details -
```
sudo dmidecode -t memory
```

---

### Post by novice_penguin on 2014-02-16
Thanks for your help!  It makes more sense now.  Cheers!

---

### Post by varunendra on 2014-02-16
You're welcome!

Please mark the thread as [SOLVED] if you think the question is properly answered. :)

---

