---
title: "Video driver problem!! I think"
date: 2017-03-18
forum: Hardware
---

### Post by benlyboy on 2017-03-18
Hi all
I will start this post with a little back ground. I have been using this hardware successfully for well over a year. The hardware in question is a Dell Inspiron micro desktop 3050 with a Intel HD Graphic chip. I have two of them as front ends for my mythbuntu setup. 
Well my backend started to show its age so I decided to build a new system and update to mythbuntu 16.04 from what I believe was 14.04. After the update on the backend the two fontend would no longer work so i updated them to 16.04, had a couple of problems getting every thing working but finely got everything happily working again.

Well I guess I wouldn’t be if that were true. I have found that after a few hours of viewing the frontends will just freeze and will have to be shutdown, by holding the power button, it will not auto shut down at the push of the button as it normally would.

I know that freezing like this is most often related to video driver issues. but why was 14.04 ok and 16.04 not...?

can you help, thanks

---

### Post by gordintoronto on 2017-03-19
Or it might be an acpi problem.

---

### Post by benlyboy on 2017-03-20
sorry but what is that?

---

### Post by gordintoronto on 2017-03-20
See Full Circle Magazine, Issue 111, Page 43.

---

### Post by slickymaster on 2017-03-20
> **gordintoronto said:**
> See Full Circle Magazine, Issue 111, Page 43.

@benlyboy:
You can grab it here: [http://fullcirclemagazine.org/2016/07/29/full-circle-magazine-111/](http://fullcirclemagazine.org/2016/07/29/full-circle-magazine-111/)

---

### Post by alexandari on 2017-03-21
Or you can ignore the magazine and look at your logs for any failing drivers after the update or kernel panics. The syslog is a start. That might cause the issue, the answer lays in the logs

---

### Post by pdc on 2017-03-21
[https://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/](https://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/)

---

