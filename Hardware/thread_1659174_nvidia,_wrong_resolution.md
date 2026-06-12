---
title: "nvidia, wrong resolution"
date: 2011-01-03
forum: Hardware
---

### Post by drudogg on 2011-01-03
ubuntu 10.10 x64

my monitor works best at 1440x900. 

my ubuntu installed at 1024x768

it looks bad and things don't take up the right amount of space.

i am running a geforce 7800gt pcie card
installed the 260.19.06 driver via restricted device manager (version current)

i can set the res up in the menu to 1152x864, but 1360x768 doesn't vibe well. it doesn't in windows either. 

i just want to get a 1440x900 @ 60hz working by default

HOW? i have tried in the past to edit config strings and what not, but i was unsuccessfil.

---

### Post by PapaNerd on 2011-01-05
Here is a possibility that has worked for me in similar situations in the past.  Add this into the "Screen" section of your /etc/X11/xorg.conf file:```
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1360x768" "1280x1024" "1152x864" "1024x768"
        EndSubSection
```You will want to create duplicate subsections for different display depths.

---

### Post by realzippy on 2011-01-05
> **PapaNerd said:**
> Here is a possibility that has worked for me in similar situations in the past.  Add this into the "Screen" section of your /etc/X11/xorg.conf file:```
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1360x768" "1280x1024" "1152x864" "1024x768"
        EndSubSection
```

Doubt this works.Guess the Hsync value is wrong;if it was correct,OP would have desired resolutions in nvidia-settings.
Can you post your current xorg.conf file?

---

### Post by drudogg on 2011-01-05
i will post it tomorrow. sorry have been away from the computer and haven't had time to check back here. 

thank you both for the responses. will post the contents of the xorg.conf after work tomorrow.

---

