---
title: "herp derp question"
date: 2011-05-25
forum: Hardware
---

### Post by thepiratefish on 2011-05-25
This is another noob question (something I'm very good at asking :p  )

is there a line i can run in the terminal that tells me what hardware I have? specifically, i'm looking for my video card. also, when I find that out, how can i find out if my driver is up to date? when I find that out, how do i update it if it needs it?

---

### Post by -Zeus- on 2011-05-25
Do you at least know the brand of your card?  Also, are you running on a desktop or laptop?

---

### Post by thepiratefish on 2011-05-25
sadly I don't. I'm using an Lenovo Thinkpad R400...that's about all I know. And I have an intel core 2 duo processor. I think that it might be ATI or something like that but I'm not sure.

---

### Post by BrandonC19 on 2011-05-25
Run the command ```
sudo lshw
``` in a terminal and copy your output into a new post with CODE tags around it. (Click the # to auto-place code tags.)

EDIT: In case you're like me and knowing the acronym of the command ill help you remember it better: [COLOR=Red]lshw[/COLOR] is [COLOR=Red]l[/COLOR]i[COLOR=Red]s[/COLOR]t[COLOR=Red] h[/COLOR]ard[COLOR=Red]w[/COLOR]are and [COLOR=Red]sudo[/COLOR] is [COLOR=Red]s[/COLOR]ubstitute[COLOR=Red] u[/COLOR]ser [COLOR=Red]do[/COLOR]

---

### Post by mikewhatever on 2011-05-25
This should tell you all there is to know:
```
lspci | grep VGA
```

The drivers is rarely uptodate, unless you run the development version. I wouldn't recommend updating it for the sake of updating, because the results may be very unpredictable.

PS: A descriptive thread title would have been nice.

---

### Post by thepiratefish on 2011-05-26
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

apparently that's why I have


sorry about not having a good thread name...I'm still getting back in the swing of the forum use thing :p

---

### Post by mikewhatever on 2011-05-26
You are welcome to tell us why you think you need a driver update. In case you were hoping to run a recent game on that, be advised that Intel graphics are not intended for gaming.

---

