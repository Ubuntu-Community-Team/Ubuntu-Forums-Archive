---
title: "Lost sound after updating packeges"
date: 2010-03-29
forum: Hardware
---

### Post by dnyanesh.3 on 2010-03-29
Hi,
 I am using Ubantu9.04 and before few days I have tried installing amsn.It promted to dependencies for following packeges : 
       1. farsight2-0.0.17
       2. gstreamer-0.10.27
After installing that I have lost sound,and the error was :

  "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

aplay -l 

gives output - sound card not found

but lspci -v  - list the sound card 

What should be the problem ? 
 
  Thanking You.

---

### Post by chessnerd on 2010-03-29
Ubuntu sound issues and I have a long relationship going back to when I first started using it, so perhaps my "experience" in this area can help you out. I understand how frustrating it can be.

Some questions:

Are you using a laptop or a desktop?

On-board (integrated) sound or a dedicated sound card?

Name of the sound card?

Name of any GStreamer plugins that you have installed for aMSN or other programs (Rythmbox, etc.)?

I have rarely gotten help with sound issues in the past, and I'm not an expert on GStreamer (which looks like the cause of your problem), but hopefully I can help you out.

---

### Post by dnyanesh.3 on 2010-03-29
**Thank You**[U][B]
[chessnerd ]("http://ubuntuforums.org/member.php?u=804379")

[/B][/U][B]  Here is providing information you enquired : -

     I am using desktop.
     Sound card info - Audio device
                                /0/100/1b
    product: 82801G (ICH7 Family) High Definition Audio Controller [8086:27D8]
                               vendor: Intel Corporation [8086]


   and the gsreamer version i have updated was - gstreamer-0.10.27.
I have also tried updating kernel module as suggested by wiki and then reconfiguring asla by module assistant.



[/B]

---

