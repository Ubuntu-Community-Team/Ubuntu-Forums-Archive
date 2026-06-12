---
title: "Palm not found"
date: 2008-08-27
forum: General Help
---

### Post by Chris_Foster on 2008-08-27
I am trying to connect my palm tungeson to my PC using the software "kpilot".
I plug in my palm, start kpilot and ask it to autodetect the location of my palm. I press the hotsnyc button on the palm and they both return a cannot make connect and a not found error.

I can't really provide much more information and I know palms are out-of-date, but they give me some games to play wile im in the car or bored by other stuff, I also want to experiment with python on palmOS (but thats another topic).

Hope someone can help :)

---

### Post by Chris_Foster on 2008-08-28
Anyone have any ideas?

---

### Post by ArgentSilver on 2008-09-14
This worked for my Palm TX under Kubuntu Hardy:

In Kpilot, select Settings-> Configure Kpilot-> General Setup-> Device. Then for 'Pilot device' enter usb: and for 'Speed' enter 115200. If you know the Username on the Palm, enter it on this page too.

Then press the Hotsync button on your Palm and it should work.

I would also note that Kpilot seems a little flaky, since my experience is the Kpilot daemon crashes about 15 sec after every hotsync!

As an aside, I'm not sure how active the Kpilot project is anymore, as it seems somewhat dated.

Edit: This assumes you are connecting your Palm with a USB connection. Most Palms have been that way for years now but if you are using a serial port then the above does not apply.

---

