---
title: "2 Webcams with Streamer"
date: 2014-01-21
forum: Hardware
---

### Post by B_Tutzer on 2014-01-21
Hello to all,
I have 2 Webcams attached to my Laptop. The built in one and a USB-Webcam. They are both recognized just fine in Ubuntu and show up in /dev/ as video0 and video1.
The Problem: I want to use video1 to capture Pictures in a Periodic Time, for that I want to use streamer by Gerd Knorr. Streamer uses video0 as default, and when i specify -i "video1" it says that it's not a valid value and gives "Camera 1" as example for a valid command. When I give "Camera 1" it uses video0 (neither "Camera 0" or "Camera 2" use video1, both display the same Error as before).
How can I specify the second Camera to be recorded by Streamer?
Thanks for your help!

---

