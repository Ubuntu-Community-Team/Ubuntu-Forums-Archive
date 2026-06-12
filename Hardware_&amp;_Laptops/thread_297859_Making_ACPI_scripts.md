---
title: "Making ACPI scripts"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by davebed on 2006-11-11
I'm quite new to dapper but I'm slowly getting used to things. My latest problem is  after installing Beryl, I find my screen blanking is no longer working. Apparently from what I've read here in the forums is that XGL doesn't support DPMS very well.

One workaround a user her found was to issue the command 
```
DISPLAY=:0 xset dpms 30
``` to set the screen to blank after 30 seconds. This works for me. 

What I want to do is learn how to create a script and make use of the ACPI events so that I can *have my screen blank using the above command after 60 seconds while on battery and blank after 180 seconds while on AC.*

Can anyone guide me towards this end? I feel I am close, but have not been able to get it to work yet. 
Thanks.

---

