---
title: "screen tair with nvidia"
date: 2021-06-22
forum: Hardware
---

### Post by supervidak64 on 2021-06-22
hello i have screen tair on my laptop that has a nvidia card with a prime display i don't know how to turn off screen tair.
I have a nvidia geforce mx450 card with nvidia driver metapackage from nvidia-driver-465.
Im running kubuntu 21.04.

Thanks in advance!

---

### Post by him610 on 2021-06-22
Not quite sure what a 'prime display' is? 
Where did you get 'nvidia-driver-465' from?
Please run the following commands from a terminal and post the results between the code tags...
```

inxi -Fxz
lshw -c display -sanitize
dpkg -l | grep nvidia

```
I may not be able to solve your problem, but maybe one of the subject matter experts will come along that can.

---

