---
title: "Thinkpad T25(T470) 18.10 facerecognition working."
date: 2018-10-21
forum: Hardware
---

### Post by j-c-9 on 2018-10-21
Hello I am very glad that under 18.10 the face recognition is working on Thinkpad T25 and probably T470 too.

[B]Thank to
[https://github.com/boltgolt/howdy](https://github.com/boltgolt/howdy)[/B]

[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=#24292E][FONT=Calibri]sudo add-apt-repository ppa:boltgolt/howdy[/FONT][/COLOR][FONT=Calibri] [/FONT]*[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=#24292E][FONT=Calibri]sudo apt update[/FONT][/COLOR][FONT=Calibri] [/FONT]*[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=#24292E][FONT=Calibri]sudo apt install howdy[/FONT][/COLOR][FONT=Calibri] [/FONT]*[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#222222][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#222222][FONT=Calibri]When installation asks about infra lighting there was no infra lighting ever. [/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#222222][FONT=Calibri]After Howdy install there was [/FONT][/COLOR][COLOR=#222222][FONT=Calibri]cv2 problem, the solution was:[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=#24292E][FONT=Calibri]sudo –H pip install opencv-python[/FONT][/COLOR][FONT=Calibri] [/FONT]*[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]It was necessary to add line[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=#24292E][FONT=Calibri]QT_X11_NO_MITSHM=1[/FONT][/COLOR]*[FONT=Calibri]* *
[/FONT][COLOR=#24292E][FONT=Calibri]to[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri] /etc/environment ([/FONT][/COLOR][COLOR=#24292E][FONT=Calibri]sudo nano /etc/environment[/FONT][/COLOR][COLOR=#24292E][FONT=Calibri])[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]Device=1 is normal camera on TP25 (TP470)[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]Device=0 is infra camera[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]It was not working, there was a green snow in Cheese program.[/FONT][/COLOR][FONT=Calibri]  In Guvcview it looks good.[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]
It was necessary to change using [/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=#24292E][FONT=Calibri]s[/FONT][/COLOR][COLOR=#24292E][FONT=Calibri]udo howdy config[/FONT][/COLOR][FONT=Calibri] [/FONT]*[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]lines[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][I][COLOR=windowtext][FONT=Calibri]device = 0
frame_width = 340[/FONT][/COLOR][FONT=Calibri] [/FONT][/I][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext]*[COLOR=windowtext][FONT=Calibri]frame_height = 340[/FONT][/COLOR][FONT=Calibri] [/FONT]*[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]There was defaults ..  -1[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]Persisting problem: If I successfully login to Ubuntu using face recognition, I must unlock keyring.[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]I use Chrome and Skype.[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]I needed to disable howdy to install plugin for hp printer using hplip-gui. Hplip-gui allways had bad password when Howdy enabled, no face recognition timeout reached.[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]Question: is it possible that  after that  ubuntu update manager said: your python installation is corrupted fix your[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri]usr/bin/python symlink[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=windowtext][COLOR=#24292E][FONT=Calibri](when I start it it starts to python 2.7)[/FONT][/COLOR][/COLOR]
[/FONT][/COLOR]
fixed  with this:
*sudo rm  /usr/bin/python*
*sudo ln -sf /usr/bin/python2.7 /usr/bin/python*

---

