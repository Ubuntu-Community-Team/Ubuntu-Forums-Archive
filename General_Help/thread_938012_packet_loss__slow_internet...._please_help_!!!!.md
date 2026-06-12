---
title: "packet loss / slow internet.... please help !!!!"
date: 2008-10-04
forum: General Help
---

### Post by smooth3006 on 2008-10-04
im so tired of my internet going slow at times. i have comcast broadband cable and it should not be like this. i even disabled & blacklisted ipv6 in ubuntu. i called comcast and they say i have 7% packet loss on my internet. they say it is either a bad modem or something on their end. i doubt it is the modem because this would happen all the time. could it be something with ubuntu and the lan config ? would the ubuntu firewall have anything to do with this ? i am not behind any router either.

i ran speedtest and here is the outcome:

download = 23773 kbps

upload = 108 kbps

:(



can you guys help me out here ? how can i see what my lan speed is set at ? there has got to be something i can do here. i notice this happens at night and in the afternoon like now.

---

### Post by Calmatory on 2008-10-04
If it happens only during certain times, it sounds like that the problem is outside, not in your machine.

Any chance to run the speedtest with different computer/operating system? You could install Ubuntu to small (i.e. 5 GB) partition of your HDD to test this.

Cable or DSL?

---

### Post by smooth3006 on 2008-10-04
> **Calmatory said:**
> If it happens only during certain times, it sounds like that the problem is outside, not in your machine.

Any chance to run the speedtest with different computer/operating system? You could install Ubuntu to small (i.e. 5 GB) partition of your HDD to test this.

Cable or DSL?

the download speed is a bit faster in vista but the upload is about the same when i have issues. i know ubuntu wouldn't cause this and my laptop is new. i doubt it is my cable modem either as it would act up all the time. 

im really confused here, is there a way to see how fast my nvidia lan adapter is set at ?

comcast is coming out monday to check it out but id love to find a fix myself.

---

### Post by smooth3006 on 2008-10-04
bump....  anyone ? 

i also posted this at launchpad. :confused:

---

### Post by Calmatory on 2008-10-04
I would bet the modem or your hardware is the problem and needs replacing. If not, then the problem remains in between your house and comcast, and that is for comcast to fix.

---

### Post by smooth3006 on 2008-10-04
> **Calmatory said:**
> I would bet the modem or your hardware is the problem and needs replacing. If not, then the problem remains in between your house and comcast, and that is for comcast to fix.

i know it's not the laptop because it's new and this happened on my old desktop pc as well. could be the cable modem but i think this would happen all the time. as of now it is resolved but earlier it was an issue. 

i also hear comcast can tether the internet so i hope thats not the case ? 

still doesn't make sense that i have 7% packet loss.

---

### Post by Calmatory on 2008-10-04
> **smooth3006 said:**
> i know it's not the laptop because it's new and this happened on my old desktop pc as well. could be the cable modem but i think this would happen all the time. as of now it is resolved but earlier it was an issue. 

i also hear comcast can tether the internet so i hope thats not the case ? 

still doesn't make sense that i have 7% packet loss.

If it is cable modem, and it usually happens during evenings, that would imply that the internet usage in your area exceeds the capabilities of the network Comcast uses around there, thus your(and others) speeds get worse as the network is being "overloaded".

And yes, Comcast throtles speeds of connections if you use P2P programs. Sad but true. :|

---

