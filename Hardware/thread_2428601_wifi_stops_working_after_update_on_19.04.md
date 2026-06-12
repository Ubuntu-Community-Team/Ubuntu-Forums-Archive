---
title: "wifi stops working after update on 19.04"
date: 2019-10-06
forum: Hardware
---

### Post by leandrobp on 2019-10-06
Hello,

I just did an usual update and my wifi isn't working anymore. I'm using a Kubuntu 19.04 on a old HP Pavilion dv4 laptop. 
How can I proceed? I'm relatively new on linux, what information should I provide?

Thanks in advance

---

### Post by SeijiSensei on 2019-10-07
I have a dv6 which I upgraded from Kubuntu 18.04 to 19.04 and now to 19.10.  It always finds my wifi adapter, an Intel Centrino. Running the command "lspci" returns a list of devices, one of which is

```
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
```

When you click on the networking icon in the panel, do you see your device appear?

Let's get one possibility out of the way.  On my machine F12 controls the wifi adapter. For some reason the normal and Fn-shift versions of the Fn keys are reversed. So if I hit F12, it turns off the wifi. Hitting it again turns it back on.  See if that helps.  If F12 doesn't matter, try Fn+F12.

---

