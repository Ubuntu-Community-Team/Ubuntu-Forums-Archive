---
title: "What does this mean? (dvd+rw-mediainfo/growisofs)"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by seanmc42 on 2006-04-02
I appended a reply to a DVD thread last night about 3 successfull burns followed by a coaster...
Now, The growisofs won't even start!
It says, "Failed to change write speed: 7056->3324"

I just switched from Memorex media (ID: RITEKD01) to TDK (ID:RICOHJPND00)
because I thought the TDK might be a better quality.

I ran dvd+rw-mediainfo and got 2 things I don't understand:
1) "Current Write Speed: 5.1x1385=7056KB/s)", &
2) "Write Speed #0: 2.4x1385=3324KB/s"

I thought the 2.4 would be the minimum wrote speed, so I changed my growisofs commandline from using -speed 1 to -speed 2.4, but I got the same error.
Does this mean I NEED to use 5.1 (->7056)? I'm afraid to try that as I'm sure I'll end up with ANOTHER $4 coaster...

Basically, I don't know what I'm doing. ;) The dvd+rw-mediainfo man page didn't offer anything in terms of interpretting its output, so I'm hoping someone here can tell me what's going on.

FYI: This is dual-layer media on an Hp dvd640 lightscribe burner. I have DMA enabled.

Thanks!

---

### Post by seanmc42 on 2006-04-02
PS> The packaging indicates the media is "up to 2.4x compatible", so I assume that means the 5.1x is the drive's setting, and would not work on this media.
Why won't the drive change?

---

