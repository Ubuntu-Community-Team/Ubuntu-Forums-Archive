---
title: "Thinkpad (T14) trackpoint buttons configuration"
date: 2024-04-18
forum: Hardware
---

### Post by para-banana on 2024-04-18
Hi all,

First of all, I am very sorry if the solution is already out there, I just didn't find it. I guess there must be a comprehensive description somewhere, but none of the things I found looked promising.

Previously, I had an X1 carbon gen10 as business laptop and was very disappointed, because it didn't have full Linux support (there are no camera drivers). Thus I picked the T14 gen4, because it also could be ordered with ubuntu preinstalled. Therefore, I assume there must be a solution.

First thing I did was disabling the Track**pad** in the BIOS. So far everything works, but two of the three Trackpoint buttons directly above the Trackpad don't work properly:

The left button works fine and does a left mouse click.

However, the middle and right mouse buttons both do a right mouse click and something else. When I click and hold one of the buttons a context menu opens and as soon as I release the button, the menu closes again.

```
root@T14:/# xinput test 'TPPS/2 Elan TrackPoint'
#### pushing and releasing the left button (ok, as expected):
button press   1 
button release 1

#### pushing and releasing the middle button (it triggers two buttons!!):
button press   3 
button release 3 
button press   2 
button release 2

#### pushing and releasing the right button (it triggers the same two buttons!!):
button press   3 
button release 3 
button press   2 
button release 2


#### holding the middle button:
button press   3
#### releasing the middle button:
button release 3 
button press   2 
button release 2 


#### holding the right button:
button press   3
#### releasing the right button:
button release 3 
button press   2 
button release 2 

```


For some reasons the middle and right buttons are configured identical and trigger >= 2 actions at once.


How can I fix this?
I'd like to configure the middle mouse button as middle mouse click and to scroll horizontally and vertically when hold and the Trackpoint moves (standard Thinkpad configuration). The right button should do a right click.

I don't remember how I set it up on my business X1C (or whether it worked out of the box), but I still have it and could look up the configs (if I would know where to look for it - I didn't find anything under /etc/X11).

There is an ArchLinux wiki that describes the srcoll setup, but it requires libraries that are not maintained anymore for > 10 years.
There are also descriptions on how to use the buttons to do something completely different, but I cant find any description that explains how to restore the default Thinkpad behavior. 
I am not expert with X11 or xinput.

My xinput list looks like this:

```
root@T14:/# xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 Elan TrackPoint                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)
```

I am using Ubuntu 22.04.4 LTS with MATE.

Please could someone give me some advise?

Thanks a lot!

---

### Post by para-banana on 2024-05-23
[closed]
Lenovo confirmed that it must be a hardware issue.
I received a replacement Thinkpad and now it is working just fine...
[/closed]

---

