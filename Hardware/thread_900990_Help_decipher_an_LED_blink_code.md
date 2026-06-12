---
title: "Help decipher an LED blink code"
date: 2008-08-25
forum: Hardware
---

### Post by andrewkk on 2008-08-25
I think the wireless LED on my [ThinkPad X60]("http://www.thinkwiki.org/wiki/Category:X60") is trying to tell me something.

It's flashing green in this pattern:
[COLOR="Green"]short short short short short short long[/COLOR]

That's 6 short, 1 long. Repeating ad infinitum. Maybe I just have some really strange network activity going on, but that sure looks like some kind of error code. I haven't noticed any problems with the wireless connection. What could it possible mean?

---

### Post by xeth_delta on 2008-08-25
I don't own a thinkpad, so I might be wrong. Is the LED you mention, the wireless LED? I believe it's just an activity/communication with the access point indication which happens to be in that pattern.

Again, I don't have a thinkpad, so I could very well be wrong, but that's what I think it is.

Hopefully another thinkpad owner can tell you more.

---

### Post by IntuitiveNipple on 2008-08-26
According to the hardware maintenance manual for the X60, page 42: "This indicator is on when the data is transmitted."

So it is probably just the way the driver is talking to the access point. Do you see a different pattern if the laptop is out of range of other WiFi devices, or the kill-switch is on?

---

### Post by andrewkk on 2008-08-26
You're right, it appears to be just a reflection of strangely rhythmic network activity. Causing greater network load made the LED illuminate accordingly.

---

