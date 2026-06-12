---
title: "[SOLVED] Brightness problem for Vaio Laptops"
date: 2008-11-20
forum: Hardware
---

### Post by Ouguiya on 2008-11-20
Hello everyone!

I hope someone here can help me out, since I am close to getting crazy on this problem.

The problem is the following: Reducing the brightness of the laptop screen does not work at all.

After searching for a long time around the internet, I found that this is a pretty known problem, but I haven't been able to find a solution thus far.

I have tried, as recommended, the "brightness applet"for the gnome panel, which did nothing. I also tried to use xbacklight, which was often praised as a good solution. However, when using it, xbacklight only tell me: "No outputs have backlight property."

Then, I tried Nvclock, which was also often confirmed to have solved the problem, but there I only receive one of two messages:
1) "Segmentation fault"
or 2) "This software only supports 6xxx to 7xxx, if you want your hardware supported, contact the author" (or something along those lines)

The end result of all this beeing, that I currently have no possible way of reducing the brightness of the laptop screen, which consumes insane amounts of energy when on battery power.

For further reference, I have posted as a html document all hardware information on my computer.

I currently have the restricted nvidia driver, v. 177 installed (which I think is the newest one.)

Thank you for any help you can give me.

Ouguiya

---

### Post by Ouguiya on 2008-11-20
Wow this already got pushed back to page 5. Does nobody here have a solution for this problem? :(

---

### Post by Yezinki on 2008-11-20
Whats yr display..Xbrite, WSVGA, WUXGA??

---

### Post by bapoumba on 2008-11-20
This may be a problem with the nvidia driver. I have a Sony Vaio with an intel chipset, and the Fn keys work.

Edit: [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444)
Have you tried from the nvidia-settings panel?

---

### Post by Ouguiya on 2008-11-21
Hello again, and thank you for the replies.

Well the problem is this: It's not just the FN keys that don't work (personally, I never use them anyway), it's just that there is not a single way to reduce the brightness of the laptop screen.

I have tried to change the brightness from the nvidia-settings panel, however, the brightness there is a "diffrent" one. It only reduces the colors, but not the light-output (so to speak) of the screen, thus not really prolonging the battery life.

I also took a look at the Bug report which you kindly provided, but sadly, I also couldn't find a good answer there, since, as I stated above, nvclock, an otherwise wonderful program, does not solve this problem.

I believe that you are right when saying that there may be a problem with the nvidia driver. Might there be any way to correct it?

Thank you again,

Ouguiya

---

### Post by Yezinki on 2008-11-21
Ouguiya

I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....

Regards,

Yezinki.

---

### Post by MartijnV on 2008-11-21
Lots of laptops experience the same or similar problems. Seems to be a problem with graphics drivers. I've got a dell latitude C610 with ati video chip. At the moment I can reduce the brightness when ubuntu is starting up and hasn't started X yet, or when I go to a terminal. (ctrl alt F2 or other F key))

---

### Post by Ouguiya on 2008-11-21
So, technically speaking, there is no real "works-every-time" solution for this at the moment, this is quite unfortunate :(

Well, I will keep looking for solutions. Should I find one, I will post it in here, so others who have the same problem (and/or laptop) can remove the bug quickly.

Thanks everyone!

Best regards,

Ouguiya

---

### Post by bapoumba on 2008-11-21
Thanks to you. It would be very nice indeed if you find something. That is the whole point of a community :)

---

### Post by Ouguiya on 2008-11-26
Well, ladies and gentlemen, to come back to this thread one final time:

I have finally solved the problem to this annoying little brightness-control.

Before I proceed with the explanation, I want to once again thank all who helped me in this.

I almost can't bring myself to tell you how this problem was solved. As is so often the case with linux problems, the answer or the solution dangles right in front of your nose, but you are too focused on the distance to realize it.

Basically, bapoumba (cheers to him by the way!), already pointed to the solution.

The link he posted was the cure to all problems. I actually ran across that link several times, but never really paid it too much attention, since it seemed like another bug report which hadn't been solved, till I read through the entire first post closly.

Solving the problem is actually quite easy. All you have to do is register on the bug launchpad site, and then simply copy / paste all the comamnds which are given there. It should be noted that you need automake and autoconfig for this to work, that's why it didn't work for me the first time.

After this, the command "sudo nvclock -S n" where n is a number between 15 and 100, should sucessfully change your brightness level (at least it did for me).

Thanks again to all who helped, and see you round.

Yours,

Ouguiya

---

### Post by bapoumba on 2008-11-26
Glad to see you got it to work Ouguiya :)
I marked the thread as solved (you can do it for your own threads in the thread tools menu).
And, BTW, you can call me a she ;)

---

