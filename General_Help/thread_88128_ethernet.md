---
title: "ethernet"
date: 2005-11-09
forum: General Help
---

### Post by rap4ever on 2005-11-09
hello 
i`m new of the Linux world 
First time i install linux and i installed Ubuntu 
i have problem with the internet i can`t join on the internet

i go on system -> administration ->networking
i activate my ethernet 

i don`t know what else i can do
can somebody to help me?

---

### Post by nszabolcs on 2005-11-09
for dsl connection use pppoeconf
```

sudo pppoeconf

```

are you on a local network ?

---

### Post by paddyg on 2005-11-09
if you've got dsl connection, you just need to choose a dhcp or static ip address configuration for your eth device (system--->administration--->networking---ethernet connection/properties), and if your router/modem is configured correctly, just launch firefox....

If you don't, just choose modem connection---properties (phone numbers, modem port etc), then activate

---

