---
title: "How do i change the webcam settings using xorg.conf?"
date: 2008-05-04
forum: Hardware
---

### Post by gottabeandrew on 2008-05-04
My webcam is a logitech quickcam sphere mp and i'm using ubuntu 8.04.

Some programs manage to use the correct settings for my webcam which is this:

v4l2: UVC camera (046d:08cc)

But other programs such as online ones only have this option:

UVC camera (046d:08cc)

which doesn't work.

There are no webcam settings showing when i open xorg.conf but obviously it does have settings and i think that by default, it's set to "UVC camera (046d:08cc)". I want to change this to "v4l2: UVC camera (046d:08cc)" but don't want to break xorg.conf but just guessing things so does anybody know what the webcam options in xorg.conf should look like and how can i get this information?

---

### Post by gottabeandrew on 2008-05-04
Bumped because i need to get this working and it's important.

---

### Post by gottabeandrew on 2008-05-04
Come on, somebody must know.

---

### Post by Keyper7 on 2008-05-04
What makes you think that it's specifically xorg.conf that should be altered?

If I remember correctly, there's an gnome application that allows you to configure the audio and video default input devices. I don't remember its name, but it should be an option in the "Administration" menu. If it's not there, open the menu editor and see if it's a not an unchecked item. I think it's "multimedia something something", sorry, my memory sucks.

Keep in mind, though, that some applications hardcode the default device to the wrong one, so that might not help depending on the application.

---

