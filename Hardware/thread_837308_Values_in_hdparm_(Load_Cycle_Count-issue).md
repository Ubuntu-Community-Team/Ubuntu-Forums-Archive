---
title: "Values in hdparm (Load Cycle Count-issue)"
date: 2008-06-22
forum: Hardware
---

### Post by pveurshout on 2008-06-22
Currently I'm fixing the well-known [load cycle count-issue]("http://ubuntuforums.org/showthread.php?t=805570") with the ugly fix provided on this forum. However, during this process I've begun to wonder what the values that "hdparm -B" can take actually *mean*. On my own system there is no difference between the values 128 up and until 191 -which all result in hundreds of cycles per hour- and values 192 to 254, which all seem to stop the harddrive from spinning down altogether. Prior to this forum post, value 191 gave me 80 cycles in half an hour, whereas value 192 resulted in no spinning down at all during many hours of laptop usage and 'idleness'.

Could there be a difference between 192 and 254 when it comes to protection from bumps and stuff, or could hdparm (atleast in my case) just as well have used only two values - 0 and 1? I'm asking this because when applying the permanent fix I'd rather use 192 than 254, if it turns out that it provides a better protection against bumps and meanwhile doesn't allow my hard drive spin down for no reason.

*The HDD temperature is constant at 35 C at all time, no matter the number of load cycles.*

---

