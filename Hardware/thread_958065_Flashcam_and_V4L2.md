---
title: "Flashcam and V4L2"
date: 2008-10-25
forum: Hardware
---

### Post by dlawler on 2008-10-25
Ok, so i set up flashcam without woes or problems. 

now, i noticed this, because i was trying to get my webcam to be recognized with anything due to the loop i made.

$ flashcam -L
Scanning devices
------
Found V4L2 Capture device: /dev/video0 (r5u870/Sony VGP-VCC6 #1)
Found V4L Video loopback input: /dev/video2
------


it set it up as /dev/_video2_

but i'm almost positive that any program is going to default search for video1. 

or maybe i am misunderstanding the entire concept.


all i want to do is be able to use Cheese with my ricoh webcam that wants to run in v4l2.


hellllllp
i've been googling strong for about 35654 days now.

---

### Post by lleachii on 2010-06-09
Please visit [https://bugs.adobe.com/jira/browse/FP-775]("https://bugs.adobe.com/jira/browse/FP-775") to track the bug report and vote for this issue.

---

