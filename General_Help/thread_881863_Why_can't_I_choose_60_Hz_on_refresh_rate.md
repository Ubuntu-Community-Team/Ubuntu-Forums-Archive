---
title: "Why can't I choose 60 Hz on refresh rate?"
date: 2008-08-06
forum: General Help
---

### Post by Muscar on 2008-08-06
Normally when using Windows or Kubuntu I have my screen set to 60 Hz, but in ubuntu I can only choose 50 or 51 Hz, why is that?

---

### Post by rEbyTer on 2008-08-06
What resolution do you have on windows,kubuntu ? But in ubuntu ?

---

### Post by unoodles on 2008-08-06
Sounds like you don't have you graphics card drivers properly setup.
What is the brand & model of your graphics card?

---

### Post by overdrank on 2008-08-06
To add to rEbyTer, what is the model of the graphics card? If nvidia have you tried using nvidia-settings to set the refresh rate?

---

### Post by Muscar on 2008-08-06
> **overdrank said:**
> To add to rEbyTer, what is the model of the graphics card? If nvidia have you tried using nvidia-settings to set the refresh rate?

I have a Nvidia 7300, how do I access the nvidia settings?

---

### Post by overdrank on 2008-08-06
> **Muscar said:**
> I have a Nvidia 7300, how do I access the nvidia settings?

Hi and if you are using Hardy then you will need to install them via synaptic manager. Then use the command ```
gksu nvidia-settings
``` in the terminal or using the alt, F2 keys.

---

### Post by rEbyTer on 2008-08-06
> To add to rEbyTer, what is the model of the graphics card? If nvidia have you tried using nvidia-settings to set the refresh rate?
I have never used Ubuntu on nVidia... :P

@Muscar please tell us if this worked...

---

### Post by Muscar on 2008-08-06
> **overdrank said:**
> Hi and if you are using Hardy then you will need to install them via synaptic manager. Then use the command ```
gksu nvidia-settings
``` in the terminal or using the alt, F2 keys.

I have the nvidia settings open but I can't find where to change the refresh rate.

---

### Post by overdrank on 2008-08-06
> **Muscar said:**
> I have the nvidia settings open but I can't find where to change the refresh rate.

On the xserver display configuration, it is to the right of the resolution. And this refresh rate in the nvidia-settings will be contradicted by the refresh rate in the ubuntu settings.

---

### Post by JPBodner on 2008-09-10
If the NVIDIA settings gizmo and Ubuntu screen resoultion gizmo contradict, which one is actually used?  And how does the setting in ccsm play into this?   I am using a 9600gt with my HP w2207 monitor.  Things are looking pretty good, but if I move windows around too fast, it looks sloppy to me.  Not sure if it's fixable or just normal.   The monitor wants 60 Hz.  I set the NVIDIA gizmo and ccsm to that.  The Ubuntu screen resolution allows me to choose 50, 51, or 105 Hz.   

Any suggestions?  Is there something wrong here?

Thanks
JB

---

### Post by kaibob on 2008-09-10
> **JPBodner said:**
> If the NVIDIA settings gizmo and Ubuntu screen resoultion gizmo contradict, which one is actually used?

Same issue here, and it's been that way as long as I can remember. The nVidia gizmo shows 60 Hz, while the Ubuntu gizmo shows 50 Hz. My monitor allows me to check the resolution it is operating at, and it shows 60 Hz. My screen is crystal sharp, so I don't worry about the discrepancy.

---

### Post by Shazaam on 2008-09-10
AFAIK the only way to get it to run at the refresh rate you desire (non default) is to manually add mode line(s) in xorg.conf.
I think it would be like this...
```
"1280x1024@60hz"
```

+ other resolutions you need ("1024x768", "800x600", etc)...
```
SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
```
Keep the quotes on modeline entries. Hardy's refresh rate is fine for me so I didn't change it. Since Hardy/nvidia lists ZERO mode lines in xorg.conf you have some editing ahead of you. Someone correct me if I am wrong.

---

