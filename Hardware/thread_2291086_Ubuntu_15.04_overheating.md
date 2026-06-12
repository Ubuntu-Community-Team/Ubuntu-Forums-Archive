---
title: "Ubuntu 15.04 overheating"
date: 2015-08-17
forum: Hardware
---

### Post by fraizor on 2015-08-17
[TABLE]
[TR]
              [TD="class: postcell"]        I have HP ENVY dv6-7357se laptop i was running windows for about a year  yesterday i switched to ubuntu <3 but i'am facing an always noisy fan and heating of my laptop


[/TD]
[/TR]
[/TABLE]


[IMG]http://i.stack.imgur.com/PgUxm.png[/IMG]


with windows i never faced overheating problems today on ubuntu my laptop turned off because of heat (i was only using vlc and firefox).
  maybe it could be an incorrect graphics card

[IMG]http://i.stack.imgur.com/6JifQ.png[/IMG]


any ideas ?
  EDIT:  [here is my laptop's specifications]("http://support.hp.com/au-en/document/c03924929") except i added 4gb of ram now it is 8gb.

---

### Post by sab7 on 2015-08-17
I think it's normal. Unity is CPU intensive. That's why I use Lubuntu.

---

### Post by QIII on 2015-08-17
No, that's not normal.  Not for an i7.

Is this a machine with hybrid Intel/NVIDIA graphics?

---

### Post by fraizor on 2015-08-17
When i bought it the shop owner told me that this have only intel GPU
i googled the model (i found it under the battery) it says it have (NVIDIA GeForce GT 635M)[ http://support.hp.com/au-en/document/c03924929]("http://support.hp.com/au-en/document/c03924929")[TABLE="class: table table-bordered table-steps"]
[TR]
[TD][/TD]
[TD]
anyway windows used to detect it as intel
[/TD]
[/TR]
[/TABLE]

---

### Post by Frogs Hair on 2015-08-17
The HP product pages are unreliable as far as hardware goes because they make different hardware configurations. The same is true for my HP model. The HP I run is using the same intel graphics as yours at a different rev with an i5. I'm using the default firmware instead of the intel package in additional drivers though. Your temps are high compared to mine. 

```
Core 0:         +38.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +42.0°C  (high = +86.0°C, crit = +100.0°C)

```

---

### Post by fraizor on 2015-08-17
sorry bro i can't catch up with what you are saying, im new to ubuntu how could i change the firmware or driver of gpu to make less heat ?

---

### Post by Frogs Hair on 2015-08-18
The terminal output in the screen shot indicates you are running intel graphics. You also have proprietary firmware installed according to the additional drivers screen-shot. I don't know that selecting do not use this device would change anything. I would also check the temperatures when not using VLC to make sure it's not due to that application.

---

