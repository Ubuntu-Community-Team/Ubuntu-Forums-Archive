---
title: "C-Media 5.1 CMI8768 (Alsa mixer)"
date: 2009-06-24
forum: Hardware
---

### Post by Gordfoster on 2009-06-24
HI all

I am very new to Ubuntu and thus far all seems to be working great except my C-Media 5.1 Surround card. I am using the CMI8768 driver and for some reason I cannot get my center speaker working. I have attempted doing what I have found on the site for fixing the issue (which sadly didn't work)  I found articles that mention editing the .asoundrc as follows 

pcm.!default {
    type             plug
    slave.pcm       "softvol"
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "ch51dup"
    }
    control {
        name        "All"
        card        0
    }
}

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
}

which I have done and rebooted, and altho I do now have an "All" control I am still not getting any center speaker. I have noticed however I do not have a "shared switch" as someone had mentioned in another thread to make sure it was turned on (as my SUB and Center share the same jack) 

If anyone can help me get this working that would be great I am kind of at a loss on what I can attempt to do next ...

Thank you for any help you can provide with this situation

---

