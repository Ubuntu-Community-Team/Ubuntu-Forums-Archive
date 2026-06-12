---
title: "Webcam"
date: 2012-08-30
forum: Hardware
---

### Post by pudgyscott on 2012-08-30
Ok, I installed Ubuntu 11.04 with the classic ubuntu desktop. I have a Logitech HD C270 webcam, which is on the UVC list of drivers. Cheese is installed and the webcam works fine in Cheese. However, in Empathy, the video call and audio call options are not available. So I tried Kopete. Also installed Jasper. In Kopete, in the settings option, my webcam works fine. If I try to invite someone to view my webcam, I get the message
"Unable to find the Jasper image conversion program. Jasper is required to render Yahoo webcam images.
 Please see [http://userbase.kde.org/Kopete/Webcam_Support](http://userbase.kde.org/Kopete/Webcam_Support) for further information."
I believe Jasper is installed correctly.

sudo apt-get install jasper libjasper-java libjasper-runtime libjasper-dev libjasper1
and
sudo apt-get install kopete libjasper-runtime

Am I missing something? Confused and frustrated. What do I need to do in order to have my webcam work in Empathy and/or Kopete?


Thanks,
Scott

---

### Post by mörgæs on 2012-08-30
First I would begin with a fresh install of 12.04.

---

### Post by pudgyscott on 2012-08-30
I initially chose Kubuntu, however, it was running too slow for me and my cam was not working in Kopete (got the jasper message), so I installed Ubuntu 10.10, reformatted the hard drive and the install went without a hitch. I then upgraded to 11.04, which also went without a hitch. Same thing. In Kopete, under preferences, my cam works fine, but not in actual chat. Same thing with Empathy, the video and audio call buttons are not being highlighted. The person/people I'm chatting with do have webcams. Frustrating.

---

### Post by mastablasta on 2012-08-31
12.04 has newer kernel => newer drivers.
 
hence the suggestions. 
 
Kubuntu may run slow on install as many indexing services are running. once everything is indexed it runs very fast. another option is to disable these services (such as akonadi, strigi and such - i forgot which they are).

---

### Post by mörgæs on 2012-08-31
Yes, 11.04 only has a month of support left. You should move to a new version anyway.

Trying the development release (12.10) is also worthwhile. If Kubuntu is too heavy then L/Xubuntu are good alternatives, at least for troubleshooting.

---

