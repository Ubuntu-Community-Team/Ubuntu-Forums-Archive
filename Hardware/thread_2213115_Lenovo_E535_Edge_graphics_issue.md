---
title: "Lenovo E535 Edge graphics issue"
date: 2014-03-24
forum: Hardware
---

### Post by alsu3 on 2014-03-24
Hello, I have a problem with the graphics card. When the video plays if the video changes fast enough(I mean when camera moves fast) there appears some stipes, looks like video changes partly. I have ubuntu 12.04. It was upgraded and it didn't help. And also sometimes the monitor lights up bright. Looks like for a split second it becomes all white. Has anybody such a problem?

---

### Post by Yellow Pasque on 2014-03-25
> When the video plays if the video changes fast enough(I mean when camera moves fast) there appears some stripes, looks like video changes partly.
It's called "tearing." Solving it is not always easy (or even possible). What GPU, driver, and desktop are you using? (Just give your entire /var/log/Xorg.0.log if unsure)

---

### Post by alsu3 on 2014-03-25
Thank you for a reply. 
Here is the [link to the file]("http://pastebin.com/TYKCc88u").
Maybe there is a version of Ubuntu which has not such a problem?

---

### Post by alsu3 on 2014-04-05
Yes, installing Ubuntu 13.10 solved the problem.

---

