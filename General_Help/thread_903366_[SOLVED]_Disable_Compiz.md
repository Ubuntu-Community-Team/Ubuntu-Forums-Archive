---
title: "[SOLVED] Disable Compiz"
date: 2008-08-28
forum: General Help
---

### Post by Aysah on 2008-08-28
I recently setup VNC on my desktop here at home and have successfully accessed it over our VPN from work and was very excited until I realized how slow it was.

Can someone perhaps show me a script I can make to disable compiz when remote desktop is in use?  Or at the very least show me how to easily enable and disable compiz from the terminal so I can do it manually?

---

### Post by DanJC on 2008-08-28
You should be able to just right click, select Change Desktop Background, click the Visual Effects tab and select None.

---

### Post by dje on 2008-08-28
```
sudo apt-get install fusion-icon
```
add:
```
fusion-icon
```
to your startup programs and an icon will appear in the system tray on the panel, right click to switch between metacity and compiz (and any other window managers you have installed)

dje

---

### Post by Aysah on 2008-08-28
> **dje said:**
> ```
sudo apt-get install fusion-icon
```
add:
```
fusion-icon
```
to your startup programs and an icon will appear in the system tray on the panel, right click to switch between metacity and compiz (and any other window managers you have installed)

dje


Will this be an automatic process when I VNC in, or will I have to do it manually?  I mean, I guess at that point it wouldnt be THAT much of a difference but automation can be wonderful  :-)   

I'm just trying to make things as seamless as possible, and so far I'm succeeding.

---

### Post by dje on 2008-08-28
no it wouldn't be automatic, you would need to right click on the icon in the system tray and select metacity

dje

---

### Post by Aysah on 2008-08-28
> **dje said:**
> no it wouldn't be automatic, you would need to right click on the icon in the system tray and select metacity

dje

It really isn't that helpful of a solution unfortunately.  For instance I literally just got to work and prior to leaving the house installed that button.  The vnc is so slow because of compiz that I can hardly even click the button to change it.  In windows Remote Desktop strips down the gui to barebones automatically upon connection.

I am ultimately looking for this type of solution.

---

### Post by dje on 2008-08-28
> **Aysah said:**
> It really isn't that helpful of a solution unfortunately.  For instance I literally just got to work and prior to leaving the house installed that button.  The vnc is so slow because of compiz that I can hardly even click the button to change it.  In windows Remote Desktop strips down the gui to barebones automatically upon connection.

I am ultimately looking for this type of solution.

could you disable compiz before you leave for work? sorry if it isn't all that helpful

dje

---

### Post by billgoldberg on 2008-08-28
Why don't you do 

```
metacity --replace
```

when using the virtual desktop?

---

### Post by Aysah on 2008-08-28
> **dje said:**
> could you disable compiz before you leave for work? sorry if it isn't all that helpful

dje

lol yeah I suppose I could.. I just figured there has to be some other way.  :-)   thanks for all the input and help though djel!

---

### Post by Aysah on 2008-09-02
> **billgoldberg said:**
> Why don't you do 

```
metacity --replace
```

when using the virtual desktop?

  I was just hoping my computer home would trigger the command "metacity --replace" when I remote in but I guess I can just do this too.  I'm an avid believer in the fewer of the steps, the happier the user.   

Thanks again for all your help everyone!!  And umm if anyone gets a little script happy and wants to share please do!   :-)

---

### Post by linkx on 2008-09-19
Did anyone ever figure out how to have compiz disabled every time a VNC connection is started? 

This could and should be a feature of gnome vnc. 

I would love to hear ideas!

---

### Post by Aysah on 2008-09-22
> **linkx said:**
> Did anyone ever figure out how to have compiz disabled every time a VNC connection is started? 

This could and should be a feature of gnome vnc. 

I would love to hear ideas!

I totally agree with you but after googling like a madmen apparently it cant.  Yes you can just disable it manually once you get in but the less steps in the process the more time for more important things.

---

### Post by drewsus on 2010-04-27
So yeah, I know this topic is pretty old, but if I found this searching so I'm sure someone else might too. 

I wrote up a script to accomplish this and figured I could share it here!

Make sure to read the comments at the beginning! (nb: add this script to your startup apps)

```
#!/bin/bash
#By Drewsus
#drewsus@gmail.com
#This is a modified script I found elsewhere. 
#It had lots of holes in it and didn't work at
#first, but the concept was sound.

#Run this on your host machine when the computer starts.

#The value for USAGE_BOUNDARY might be different
#for you. Experiment to find a good value. 
#A good way to do this is to run the section between
#the two "#*"s on a loop and connect and disconnect 
#from your client machine to get an idea of what values
#to use. Typically, the value when your client is not 
#connected to your host (aka vino is idle) will always
#be the same and you should just add 600-1000 to the 
#idle value to get your USAGE_BOUNDARY values



vpid=$(pgrep vino)
USAGE_BOUNDARY=33000

while :
do
#*
MEM=$(ps -p ${vpid} -o vsz,pid | grep ${vpid} |sed "s/ ${vpid}//g" | tr -d ' ')
echo -e "\e[1mVino memory usage\e[0m: ${MEM} @ $(date +%H:%M:%S)"
#*
if [ ${MEM} -lt ${USAGE_BOUNDARY} ];then
	META_CHECK=$(pgrep -c metacity)
	if [ ${META_CHECK} -gt 0 ];then
		compiz --replace & disown
		sleep 3s
		killall gnome-panel
		#echo "compiz --replace & disown"
	fi
else
	echo "Vino is running. Will disable compiz if it is running"
	COMP_CHECK=$(pgrep -c compiz)
	if [ ${COMP_CHECK} -gt 0 ];then
		metacity --replace & disown
		#echo "metacity --replace & disown"
	fi
fi

sleep 5s

done
```

Goodluck!
Drewsus

---

### Post by drewsus on 2010-04-27
And I just realized that maybe people might like to use this to disable compiz on their HOST machine instead of or as well as. 
Well, its pretty simple. 

Just change the line:
```
vpid=$(pgrep *vino*)
```
to:
```
vpid=$(pgrep **vinagre**)
```

And of course:
```
echo "*Vino* is running. Will disable compiz if it is running"
```
to:
```
echo "**Vinagre** is running. Will disable compiz if it is running"
```

And change "**USAGE_BOUNDARY**" accordingly.

Drew

---

### Post by JoeGoalie on 2010-07-19
Hmm, I tried making this script.  Now my machine constantly runs in metacity.  Is there a way to set it up so that it only runs in metacity when a VNC is actually connected?  I'd like to just have my server run all the time in case I want to connect and then it automatically switch to metacity when I do connect.

---

