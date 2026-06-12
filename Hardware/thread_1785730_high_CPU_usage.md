---
title: "high CPU usage"
date: 2011-06-18
forum: Hardware
---

### Post by lohithmv on 2011-06-18
Hi,

I am using ubuntu 10.04.
Hardware :
Dell inspiron i3,4GB RAM,500GB HDD.
load is always high on mylaptop,it will never come down below 1.5,even in the ideal state,I am new to ubuntu.
 whats the avg load for decent usage machine(with couple windows tab and few browser windows) ? or anything below is 2 is common ?
Please someone help me on this.

-Lohith

---

### Post by sanderj on 2011-06-18
How do you measure CPU load? Which tool do you use? top, or uptime, or the GUI, or ...

And what's the "1.5"? Percentage (which is low), or the mean number of waiting processes, or ... ?

---

### Post by lohithmv on 2011-06-18
I used "uptime",
1.5 is the first value out of 3 value.

let me know if you need some more info.

---

### Post by sanderj on 2011-06-18
> **lohithmv said:**
> I used "uptime",
1.5 is the first value out of 3 value.

let me know if you need some more info.

I must confess I use 'uptime' myself too. I start to worry if the number is 3 or 4 or more. My current uptime (while I'm downloading):

sander@R540:~$ uptime
 22:04:32 up  1:31,  3 users,  load average: 1.30, 1.16, 1.08
sander@R540:~$



However, what does System Monitor (System -> Administration -> System Monitor, then tab Resources) show you? My four CPU's are all between 3% and 25%.
If you have a high CPU usage percentage, in the tab Processes, you can sort the CPU column and see which process is causing that.

---

### Post by lohithmv on 2011-06-18
one of the backup process was using high CPU(from processes tab) and i killed it now its below 1.
Thanks for the quick reply.

---

### Post by Gh0zt36 on 2011-06-18
im having a simalar problem im using cpu freq scaling monitor applet added to panel and it idles @ 46% on a intel pentium t3400 2.16 ghz dual core ... thats super high for idle isnt it ?

Edit : ok i went into system monitor and looked at resources and that cpu scaling monitor applet is straight lying to me the system monitor has it idling between 3-19%  per processor so i guess issue is solved

---

