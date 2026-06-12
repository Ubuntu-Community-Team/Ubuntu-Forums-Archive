---
title: "Enabling the fingerprint reader on a Sony Vaio Series G"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by danOMD on 2007-12-29
Hi,

Firstly please let me say hello to everyone here as this is my first post and these are my first days of running Ubuntu 7.10 ever.

I have a G Series Sony Vaio Laptop that comes with a built-in fingerprint reader for authorisation purpouses. I don't think it has been reconised in the hardware list. Is there any way I can manage this device with a programme under Linux/Ubuntu 7.10?

Thanks for your help, any advice will be greatly appreciated!

Dan

---

### Post by danOMD on 2007-12-30
Hi,

Okay, so far I've managed to install the drivers for the reader (thinkfinger), however when I try typing tf-tool --acquire I get the following message:

Could not acquire fingerprint (communication with fingerprint reader failed).

Has anyone got the same problem?

Thanks

Dan

---

### Post by Ashex on 2007-12-30
Did you run the command as root?

---

### Post by danOMD on 2007-12-30
Yes, I did.

---

### Post by zekonology on 2008-06-11
try run the command without 'sudo' :


tf-tool --acquire

---

### Post by lawlezz on 2008-07-03
same problem here.. no luck yet.. Anyone has? I'm using Vaio G too.. Running on Hardy Heron...

Btw Dan, Did you have problem with the sound output level & MMC card?

---

