---
title: "Webcam software"
date: 2005-11-10
forum: General Help
---

### Post by WetWilly on 2005-11-10
Anyone knows of any software/script that takes pictures from a webcam whenever it senses movement and then uploads the files to an ftpserver in the instance they are created??

I want to use this as a kind of surveillance in my apartment like I once read some guy did and busted a burglar! :cool:

---

### Post by invalid on 2005-11-10
Camsource has an option for motion detection.

From the config file, here is some information:

```
		<!--
			A simple motion detection filter (not active by
			default), which simply swallows the frame if
			no motion was detected, making the receiving
			module wait for a more interesting picture.
			Useful for filewrite of ftpup uses, and not so
			useful for live viewing modules.
			
			"Pixeldiff" is the value which is used to decide
			whether one pixel of the new image is different
			from the same pixel of the previous image. The
			value is a tolerance value in percent. 0 means
			the pixel will only be considered equal if it
			is indeed exactly equal, otherwise it will be
			considered different. 100 means	the pixel will
			always be considered equal. Raise this value if
			your camera produces a lot of noise.
			
			"Minthres" and "maxthres" specify how many
			percent of the pixels of the image must be
			different to trigger the motion detection. If
			the percentage is outside this range, the
			detection won't trigger. There's an upper limit
			to tag massive image changes (such as the light
			being switched on or off) as uninteresting.
			Raise maxthres to 100 to disable this behavior.
			
			If no motion is detected, the filter will wait
			"delay" milliseconds (1/1000 seconds) before
			grabbing another image and checking it for
			motion.
		-->

```

Cheers,
Cb

---

### Post by WetWilly on 2005-11-10
Thanks :) gonna try it out

Edit: Argh, latest release iss from april 2003 and when building from source I get stuck in dependency hell ..

This on the other hand seem to work even better:

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

Gonna try that one now ^^

---

### Post by bignate on 2005-11-16
Hello,

If anyone is interested and comes searching here for a way to get camsource to compile, I got it to work.

You probably have to install libpng and libxml to get it to compile.

apt-get install libjpeg-progs libjpeg-mmx-dev
apt-get install libxml-dev

I am not sure if I needed all those files, but that is what I installed, the libxml is for gnome development, but it most likely pulled in the header files I needed so there is the info.

Using the 0.7.0 sources, untar them, cd to newly created directory and then in src/  open the mod_handle.c file and on lines 309-310 edit it from:

inuse:
    }

to:

inuse:
        ;
    }

Then cd .. 
./configure
make
sudo make install

Edit the outputted camsource.conf.example ( I just renamed/moved it to my home dir ~/.camsourcerc) and then edit it with the needed values.  Then start the software with 'camsource ~/.camsourcerc'

HTH

---

