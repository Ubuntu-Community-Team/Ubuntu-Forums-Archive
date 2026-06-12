---
title: "Ubuntu Netbook Remix 10.10 on Lenovo S10-3"
date: 2011-02-17
forum: Hardware
---

### Post by slimeph on 2011-02-17
Followed the instructions on how to make a bootable USB (step 2 of [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)) and it started with error messages only.

How can I get the error message to present it here?

---

### Post by mikewhatever on 2011-02-17
If I had a digital camera, I'd take a picture, otherwise, wrote it down on a piece of paper.

---

### Post by slimeph on 2011-02-17
Tried Xubuntu before and usually it does not give any console error message after the splash screen. UNR 10.10 runs then after the splash screen I've got the whole console thing with lots of texts then it will hang in there.

Will post back with pictures if needed.

---

### Post by mikewhatever on 2011-02-17
That Lenovo model is mentioned in Maverick's release notes:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)
> Lenovo S10-3 systems don't boot. Temporary workaround: add "intel_idle.max_cstate=0" as a kernel paremeter at boot (634702). A fix already exists that will be available only at release time (647071).



---

### Post by slimeph on 2011-02-18
thanks mike! that worked. how does updates in ubuntu worked? should i download another cd image?

---

### Post by michaelschell on 2011-03-03
Gents, I have the same issue but struggle to understand how/when I can enter the needed sequence. I have no linux skills....could you precisely indicate what to do? I have a usb stick with version 10.10 for netbook, works perfect on my office laptop but on my Lenovo 10-3....
 
thx

---

### Post by slimeph on 2011-03-03
What I did was to press "e" during bootup (splash screen) then it will give you the line with the kernel parameters. scroll to the end and type "intel_idle.max_cstate=0" without the quotes.

Press ENTER and you're done. :)

---

