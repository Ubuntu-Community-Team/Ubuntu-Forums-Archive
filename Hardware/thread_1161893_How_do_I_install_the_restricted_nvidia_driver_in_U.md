---
title: "How do I install the restricted nvidia driver in Ubuntu 9.04 'Jaunty'?"
date: 2009-05-17
forum: Hardware
---

### Post by BrownCoal on 2009-05-17
Hello,

I have made a clean install of Ubuntu 9.04 'Jaunty Jackalope'.

Previously I was using Ubuntu 8.10 'Intrepid Ibex', and it was working with full 3d-acceleration using the closed-source Nvidia driver, including automatic fan control through coolbits.

Unfortunately with Jaunty I can't find any clear way of installing the closed-source Nvidia driver. There hasn't been the prompt of 'restricted driver may be needed' as in Intrepid, and when I go to Restricted Drivers Manager it states 'no restricted drivers are in use' -- it does not display the installed Nvidia AGP GeForce 6600GT or any other hardware.

I then tried Synaptic Package Manager, checked that 'restricted drivers' repository was enabled, then searched for 'nvidia', but everything that showed up was already installed (with the green checkbox).

I looked at the official documentation page on [_[COLOR="Red"]restricted drivers[/COLOR]_]("https://help.ubuntu.com/community/RestrictedDrivers#NVIDIA"), that linked to the [_[COLOR="Red"]RestrictedDrivers/NVIDIA[/COLOR]_]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?action=show&redirect=RestrictedDrivers%2FNVIDIA") page, but it only has instructions up to Ubuntu versions 8.10.

I searched for 'nvidia driver' on [[COLOR="Red"]_Launchpad_[/COLOR]]("https://answers.launchpad.net/ubuntu/+questions?field.search_text=nvidia+driver&field.sort=NEWEST_FIRST&field.sort-empty-marker=1&field.actions.search=Search&field.language=en&field.language-empty-marker=1&field.status=OPEN&field.status=NEEDSINFO&field.status=ANSWERED&field.status=SOLVED&field.status-empty-marker=1"). I found one variation of installation instructions on [[COLOR="Red"]_this_[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/nvidia-common/+question/65765#10") entry (tenth post), and another on [[COLOR="Red"]_this_[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/xorg/+question/65690") entry (also the tenth post).

I found [[COLOR="Red"]_this_[/COLOR]]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") set of instructions via Google.

And finally I didn't find any relevant post on the Ubuntu forum.

What instructions should I be following?

---

### Post by coffeecat on 2009-05-17
> **BrownCoal said:**
> when I go to Restricted Drivers Manager it states 'no restricted drivers are in use' -- it does not display the installed Nvidia AGP GeForce 6600GT or any other hardware.

Do you mean System -> Adminstration -> Hardware Drivers? Because that doesn't tell you which Nvidia card you are using, but it does prompt you with the recommended driver. However, I was helping someone to install 9.04 a couple of weeks ago, and it took some time before Hardware Drivers prompted us with anything at all. I mean an hour or so. That may be because I was running a simple script with a whole lot of apt-get this and that to get the system up to date and with useful stuff installed.

Do a Reload from Synaptic and then close Synaptic and check Hardware Drivers again. 

If that doesn't work, try installing this lot from Synaptic:

nvidia-glx-180
nvidia-common
nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-settings.

That should set itself up - I would hope.

---

### Post by BrownCoal on 2009-05-21
Well I installed all the latest updates and then went to Restricted Drivers Manager and the option to activate/install the Nvidia driver was present. So either installing the updates or just reloading the Update Manager and has eliminated the need to do the dreaded manual video driver installation.

---

