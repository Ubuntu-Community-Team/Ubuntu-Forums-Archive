---
title: "webcam logitech c210 and skype"
date: 2012-09-20
forum: Hardware
---

### Post by Dr Berta on 2012-09-20
Hi all,
I'v just bougth the webcam logitech c210 and after the installation on my ubuntu 12.04 almost everything is working. The only thing that is not working is the microphone integrated into the webcam with Skype.
I've verified that it is recognized and that it works with the sound recorder.
The audio controller doen't show the microphone presence but opening the properties it shows with the meter that the microphone is working. Pavucontrol instead shows that the meter freezes after 1-2 seconds. Since Skype uses pulseaudio to control the audio, here the microphone doesn't work.

I looked around in the forum to find a solution but without good esults
Do you have any ideas on how to solve the problem?
Thanks

---

### Post by Dr Berta on 2012-09-30
I finally found the way to solve the problem.
The solution is:
1. open pavucontrol and go into the recorder folder (where nothing is shown)
2. Start the sound test service of Skype
3. In that moment you can see in the recorder folder that skype is trying to use the microphone, click on the input device selection and choose usb microphone
That's all. :D

I hope this could be useful to other people

Bye ):P

---

