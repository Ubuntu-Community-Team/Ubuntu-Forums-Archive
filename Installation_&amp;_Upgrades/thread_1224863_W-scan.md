---
title: "W-scan"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2009-07-27
Does anyone know how to use w-scan

---

### Post by QuanTime on 2010-01-15
w_scan -c[COUNTRY]

replace [COUNTRY] with your country code, such as US for america, FR for france, AU for australia.  Hope this helps.. even tho its hugely late.. might help others one day ;)

try

```

man w_scan

```
for some info on it.

---

### Post by Fitch on 2011-04-18
Tried w-scan, but no matter what I put in as -c (i.e -c UK),  I get:
COUNTRY CODE IS NOT DEFINED. FALLING BACK TO "DE"

---

### Post by jc2038 on 2011-05-14
Try w_scan -h   which is an invalid command but outputs a help screen
it tells you that w_scan -H   gives further help
then try   w_scan -c ?

which outputs all available country codes  you will see that the united kingdom is GB *not* UK in the list

then if you want output suitable for mplayer or vlc 
run  w_scan -c GB -X >channels.conf  which will create a file channels.conf
this will take maybe 7 minutes to run through the scanning process 

you can run   w_scan -c GB -X  first which will output to the screen

otherwise you will be waiting around 7 minutes not knowing if there is any output. w_scan should display your card details at the beginning if it can
identify your card or usb stick 

if it does not,  check that your DVB-T card or stick is installed properly ie correct firmware loaded etc see the output of running dmesg or look in /var/log/messages


load channels.conf into a text editor down at the bottom of the file
there is a block of the channels that have been found 
example:
dumping lists (109 services)
BBC ONE Scot(BBC):634166670:INVERSION_AUTO:BANDWIDTH_8_ .....
etc etc
TOPUP Anytime3(TUTV):658166670:INVERSION_AUTO:BANDWIDTH_8_...
Done.

channels.conf should only contain this block of in my case 109 lines
get rid of extra lines like done Try w_scan -h   which is an invalid command but outputs a help screen
it tells you that w_scan -H   gives further help
then try   w_scan -c ?

which outputs all available country codes  you will see that the united kingdom is GB *not* UK in the list

then if you want output suitable for mplayer or vlc 
run  w_scan -c GB -X >channels.conf  which will create a file channels.conf
this will take maybe 7 minutes to run through the scanning process 

you can run   w_scan -c GB -X  first which will output to the screen

otherwise you will be waiting around 7 minutes not knowing if there is any output. w_scan should display your card details at the beginning if it can
identify your card or usb stick 

if it does not,  check that your DVB-T card or stick is installed properly ie correct firmware loaded etc see the output of running dmesg or look in /var/log/messages


load channels.conf into a text editor down at the bottom of the file
there is a block of the channels that have been found 
example:
dumping lists (109 services)
BBC ONE Scot(BBC):634166670:INVERSION_AUTO:BANDWIDTH_8_ .....
etc etc
TOPUP Anytime3(TUTV):658166670:INVERSION_AUTO:BANDWIDTH_8_...
Done.

channels.conf should only contain this block of in my case 109 lines
get rid of extra lines like done and dumping lists 

for mplayer put the file in /etc/mplayer directory where mplayer.conf input.conf are

mplayer dvb://'BBC ONE Scot(BBC)'  will play that channel 

gnome-mplayer has an option on the file menu to play tv i have never got 
that to work, if you have gnome-mplayer you also have mplayer which can be run from a terminal window

vlc file menu/streaming/capture device/dvb-t starts a scan but never finds any channels it needs initial values to be entered and possibly dvb-utils installed on the system some day i might look into how to do it meanwhile 
the method below works for me 
vlc --playlist-tree tv.conf radio.conf 

for vlc
vlc channels.conf   will load all the channels into the playlist 
or run vlc then open your channels.conf file from the file menu or drag and drop channels.conf onto a running copy of vlc

other options 
w_scan -c GB -X -E 0 -O 0 >channels.conf  excludes encripted and other channels reduces list to 65 channels 

-k	generate channels.dvb for kaffeine

	-X	tzap/czap/xine output instead of vdr channels.conf
	-x	generate initial tuning data for (dvb-)scan

note -X and-x are different output types 

w_scan -c GB -X -T 0 >radio.conf	

vlc needs filename to end with .conf for DVB-T but you can use multiple playlists and other playlist formats for music etc 


mplayer dvb://'BBC ONE Scot(BBC)' -dumpstream -dumpfile your-file.ts.mpg
uses less than 20% cpu recording the stream into a file at around 1gbyte per hour for standard definition tv,  hd will use up much more space

mplayer can replay the file but it is still a transport stream as it was broadcast ie seeking forward in the file while possible is hit and miss

vlc will not be able to play it, solution is to convert to a program stream
using ffmpeg or mencoder
eg ffmpeg -i your-file.ts.mpg -target pal-dvd -vcodec copy -acodec copy your-file.ps.mpg   because we are not converting the file using a different codec this is fast 700+ fps on a ancient 10 year old amd 1.1ghz computer

now vlc can play the file but it is still the original stream ie a mix of mpeg2 video mp3 audio at different bitrates and 4:3 and 16:9 aspect ratios (adverts usually 16:9) some channels are all 16:9 and sometimes interlaced content it all depends on the broadcaster
it does not really matter as long as mplayer or gnome-player and vlc can play it.

Try w_scan -h   which is an invalid command but outputs a help screen
it tells you that w_scan -H   gives further help
then try   w_scan -c ?

which outputs all available country codes  you will see that the united kingdom is GB *not* UK in the list

then if you want output suitable for mplayer or vlc 
run  w_scan -c GB -X >channels.conf  which will create a file channels.conf
this will take maybe 7 minutes to run through the scanning process 

you can run   w_scan -c GB -X  first which will output to the screen

otherwise you will be waiting around 7 minutes not knowing if there is any output. w_scan should display your card details at the beginning if it can
identify your card or usb stick 

if it does not,  check that your DVB-T card or stick is installed properly ie correct firmware loaded etc see the output of running dmesg or look in /var/log/messages


load channels.conf into a text editor down at the bottom of the file
there is a block of the channels that have been found 
example:
dumping lists (109 services)
BBC ONE Scot(BBC):634166670:INVERSION_AUTO:BANDWIDTH_8_ .....
etc etc
TOPUP Anytime3(TUTV):658166670:INVERSION_AUTO:BANDWIDTH_8_...
Done.

channels.conf should only contain this block of in my case 109 lines
get rid of extra lines like done and dumping lists 

for mplayer put the file in /etc/mplayer directory where mplayer.conf input.conf are

mplayer dvb://'BBC ONE Scot(BBC)'  will play that channel 

gnome-mplayer has an option on the file menu to play tv i have never got 
that to work, if you have gnome-mplayer you also have mplayer which can be run from a terminal window

vlc file menu/streaming/capture device/dvb-t starts a scan but never finds any channels it needs initial values to be entered and possibly dvb-utils installed on the system some day i might look into how to do it meanwhile 
the method below works for me 
vlc --playlist-tree tv.conf radio.conf 

for vlc
vlc channels.conf   will load all the channels into the playlist 
or run vlc then open your channels.conf file from the file menu or drag and drop channels.conf onto a running copy of vlc

other options 
w_scan -c GB -X -E 0 -O 0 >channels.conf  excludes encripted and other channels reduces list to 65 channels 

-k	generate channels.dvb for kaffeine

	-X	tzap/czap/xine output instead of vdr channels.conf
	-x	generate initial tuning data for (dvb-)scan

note -X and-x are different output types 

w_scan -c GB -X -T 0 >radio.conf	

vlc needs filename to end with .conf for DVB-T but you can use multiple playlists and other playlist formats for music etc 


mplayer dvb://'BBC ONE Scot(BBC)' -dumpstream -dumpfile your-file.ts.mpg
uses less than 20% cpu recording the stream into a file at around 1gbyte per hour for standard definition tv,  hd will use up much more space

mplayer can replay the file but it is still a transport stream as it was broadcast ie seeking forward in the file while possible is hit and miss

vlc will not be able to play it, solution is to convert to a program stream
using ffmpeg or mencoder
eg ffmpeg -i your-file.ts.mpg -target pal-dvd -vcodec copy -acodec copy your-file.ps.mpg   because we are not converting the file using a different codec this is fast 700+ fps on a ancient 10 year old amd 1.1ghz computer

now vlc can play the file but it is still the original stream ie a mix of mpeg2 video mp3 audio at different bitrates and 4:3 and 16:9 aspect ratios (adverts usually 16:9) some channels are all 16:9 and sometimes interlaced content it all depends on the broadcaster
it does not really matter as long as mplayer or gnome-player and vlc can play it.



w_scan does not need initial data other than country code
 dvb-utils package which i understand needs 
initial data to be obtained possibly this 
w_scan output  
-x	generate initial tuning data for (dvb-)scan


ps
if using  -A N	specify ATSC type
 see this w_scan bug report 
[https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786](https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786)
 










w_scan does not need initial data other than country code
 dvb-utils package which i understand needs 
initial data to be obtained possibly this 
w_scan output  
-x	generate initial tuning data for (dvb-)scan


ps
if using  -A N	specify ATSC type
 see this w_scan bug report 
[https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786](https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786)
 








and dumping lists 

for mplayer put the file in /etc/mplayer directory where mplayer.conf input.conf are

mplayer dvb://'BBC ONE Scot(BBC)'  will play that channel 

gnome-mplayer has an option on the file menu to play tv i have never got 
that to work, if you have gnome-mplayer you also have mplayer which can be run from a terminal window

vlc file menu/streaming/capture device/dvb-t starts a scan but never finds any channels it needs initial values to be entered and possibly dvb-utils installed on the system some day i might look into how to do it meanwhile 
the method below works for me 
vlc --playlist-tree tv.conf radio.conf 

for vlc
vlc channels.conf   will load all the channels into the playlist 
or run vlc then open your channels.conf file from the file menu or drag and drop channels.conf onto a running copy of vlc

other options 
w_scan -c GB -X -E 0 -O 0 >channels.conf  excludes encripted and other channels reduces list to 65 channels 

-k	generate channels.dvb for kaffeine

	-X	tzap/czap/xine output instead of vdr channels.conf
	-x	generate initial tuning data for (dvb-)scan

note -X and-x are different output types 

w_scan -c GB -X -T 0 >radio.conf	

vlc needs filename to end with .conf for DVB-T but you can use multiple playlists and other playlist formats for music etc 


mplayer dvb://'BBC ONE Scot(BBC)' -dumpstream -dumpfile your-file.ts.mpg
uses less than 20% cpu recording the stream into a file at around 1gbyte per hour for standard definition tv,  hd will use up much more space

mplayer can replay the file but it is still a transport stream as it was broadcast ie seeking forward in the file while possible is hit and miss

vlc will not be able to play it, solution is to convert to a program stream
using ffmpeg or mencoder
eg ffmpeg -i your-file.ts.mpg -taTry w_scan -h   which is an invalid command but outputs a help screen
it tells you that w_scan -H   gives further help
then try   w_scan -c ?

which outputs all available country codes  you will see that the united kingdom is GB *not* UK in the list

then if you want output suitable for mplayer or vlc 
run  w_scan -c GB -X >channels.conf  which will create a file channels.conf
this will take maybe 7 minutes to run through the scanning process 

you can run   w_scan -c GB -X  first which will output to the screen

otherwise you will be waiting around 7 minutes not knowing if there is any output. w_scan should display your card details at the beginning if it can
identify your card or usb stick 

if it does not,  check that your DVB-T card or stick is installed properly ie correct firmware loaded etc see the output of running dmesg or look in /var/log/messages


load channels.conf into a text editor down at the bottom of the file
there is a block of the channels that have been found 
example:
dumping lists (109 services)
BBC ONE Scot(BBC):634166670:INVERSION_AUTO:BANDWIDTH_8_ .....
etc etc
TOPUP Anytime3(TUTV):658166670:INVERSION_AUTO:BANDWIDTH_8_...
Done.

channels.conf should only contain this block of in my case 109 lines
get rid of extra lines like done and dumping lists 

for mplayer put the file in /etc/mplayer directory where mplayer.conf input.conf are

mplayer dvb://'BBC ONE Scot(BBC)'  will play that channel 

gnome-mplayer has an option on the file menu to play tv i have never got 
that to work, if you have gnome-mplayer you also have mplayer which can be run from a terminal window

vlc file menu/streaming/capture device/dvb-t starts a scan but never finds any channels it needs initial values to be entered and possibly dvb-utils installed on the system some day i might look into how to do it meanwhile 
the method below works for me 
vlc --playlist-tree tv.conf radio.conf 

for vlc
vlc channels.conf   will load all the channels into the playlist 
or run vlc then open your channels.conf file from the file menu or drag and drop channels.conf onto a running copy of vlc

other options 
w_scan -c GB -X -E 0 -O 0 >channels.conf  excludes encripted and other channels reduces list to 65 channels 

-k	generate channels.dvb for kaffeine

	-X	tzap/czap/xine output instead of vdr channels.conf
	-x	generate initial tuning data for (dvb-)scan

note -X and-x are different output types 

w_scan -c GB -X -T 0 >radio.conf	

vlc needs filename to end with .conf for DVB-T but you can use multiple playlists and other playlist formats for music etc 


mplayer dvb://'BBC ONE Scot(BBC)' -dumpstream -dumpfile your-file.ts.mpg
uses less than 20% cpu recording the stream into a file at around 1gbyte per hour for standard definition tv,  hd will use up much more space

mplayer can replay the file but it is still a transport stream as it was broadcast ie seeking forward in the file while possible is hit and miss

vlc will not be able to play it, solution is to convert to a program stream
using ffmpeg or mencoder
eg ffmpeg -i your-file.ts.mpg -target pal-dvd -vcodec copy -acodec copy your-file.ps.mpg   because we are not converting the file using a different codec this is fast 700+ fps on a ancient 10 year old amd 1.1ghz computer

now vlc can play the file but it is still the original stream ie a mix of mpeg2 video mp3 audio at different bitrates and 4:3 and 16:9 aspect ratios (adverts usually 16:9) some channels are all 16:9 and sometimes interlaced content it all depends on the broadcaster
it does not really matter as long as mplayer or gnome-player and vlc can play it.
Try w_scan -h   which is an invalid command but outputs a help screen
it tells you that w_scan -H   gives further help
then try   w_scan -c ?

which outputs all available country codes  you will see that the united kingdom is GB *not* UK in the list

then if you want output suitable for mplayer or vlc 
run  w_scan -c GB -X >channels.conf  which will create a file channels.conf
this will take maybe 7 minutes to run through the scanning process 

you can run   w_scan -c GB -X  first which will output to the screen

otherwise you will be waiting around 7 minutes not knowing if there is any output. w_scan should display your card details at the beginning if it can
identify your card or usb stick 

if it does not,  check that your DVB-T card or stick is installed properly ie correct firmware loaded etc see the output of running dmesg or look in /var/log/messages


load channels.conf into a text editor down at the bottom of the file
there is a block of the channels that have been found 
example:
dumping lists (109 services)
BBC ONE Scot(BBC):634166670:INVERSION_AUTO:BANDWIDTH_8_ .....
etc etc
TOPUP Anytime3(TUTV):658166670:INVERSION_AUTO:BANDWIDTH_8_...
Done.

channels.conf should only contain this block of in my case 109 lines
get rid of extra lines like done and dumping lists 

for mplayer put the file in /etc/mplayer directory where mplayer.conf input.conf are

mplayer dvb://'BBC ONE Scot(BBC)'  will play that channel 

gnome-mplayer has an option on the file menu to play tv i have never got 
that to work, if you have gnome-mplayer you also have mplayer which can be run from a terminal window

vlc file menu/streaming/capture device/dvb-t starts a scan but never finds any channels it needs initial values to be entered and possibly dvb-utils installed on the system some day i might look into how to do it meanwhile 
the method below works for me 
vlc --playlist-tree tv.conf radio.conf 

for vlc
vlc channels.conf   will load all the channels into the playlist 
or run vlc then open your channels.conf file from the file menu or drag and drop channels.conf onto a running copy of vlc

other options 
w_scan -c GB -X -E 0 -O 0 >channels.conf  excludes encripted and other channels reduces list to 65 channels 

-k	generate channels.dvb for kaffeine

	-X	tzap/czap/xine output instead of vdr channels.conf
	-x	generate initial tuning data for (dvb-)scan

note -X and-x are different output types 

w_scan -c GB -X -T 0 >radio.conf	

vlc needs filename to end with .conf for DVB-T but you can use multiple playlists and other playlist formats for music etc 


mplayer dvb://'BBC ONE Scot(BBC)' -dumpstream -dumpfile your-file.ts.mpg
uses less than 20% cpu recording the stream into a file at around 1gbyte per hour for standard definition tv,  hd will use up much more space

mplayer can replay the file but it is still a transport stream as it was broadcast ie seeking forward in the file while possible is hit and miss

vlc will not be able to play it, solution is to convert to a program stream
using ffmpeg or mencoder
eg ffmpeg -i your-file.ts.mpg -target pal-dvd -vcodec copy -acodec copy your-file.ps.mpg   because we are not converting the file using a different codec this is fast 700+ fps on a ancient 10 year old amd 1.1ghz computer

now vlc can play the file but it is still the original stream ie a mix of mpeg2 video mp3 audio at different bitrates and 4:3 and 16:9 aspect ratios (adverts usually 16:9) some channels are all 16:9 and sometimes interlaced content it all depends on the broadcaster
it does not really matter as long as mplayer or gnome-player and vlc can play it.



w_scan does not need initial data other than country code
 dvb-utils package which i understand needs 
initial data to be obtained possibly this 
w_scan output  
-x	generate initial tuning data for (dvb-)scan


ps
if using  -A N	specify ATSC type
 see this w_scan bug report 
[https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786](https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786)
 











w_scan does not need initial data other than country code
 dvb-utils package which i understand needs 
initial data to be obtained possibly this 
w_scan output  
-x	generate initial tuning data for (dvb-)scan


ps
if using  -A N	specify ATSC type
 see this w_scan bug report 
[https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786](https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786)
 








rget pal-dvd -vcodec copy -acodec copy your-file.ps.mpg   because we are not converting the file using a different codec this is fast 700+ fps on a ancient 10 year old amd 1.1ghz computer

now vlc can play the file but it is still the original stream ie a mix of mpeg2 video mp3 audio at different bitrates and 4:3 and 16:9 aspect ratios (adverts usually 16:9) some channels are all 16:9 and sometimes interlaced content it all depends on the broadcaster
it does not really matter as long as mplayer or gnome-player and vlc can play it.



w_scan does not need initial data other than country code
 dvb-utils package which i understand needs 
initial data to be obtained possibly this 
w_scan output  
-x	generate initial tuning data for (dvb-)scan


ps
if using  -A N	specify ATSC type
 see this w_scan bug report 
[https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786](https://bugs.launchpad.net/ubuntu/+source/w-scan/+bug/771786)

---

### Post by jc2038 on 2011-05-14
sorry about that garbled post the forum logged me out
towards the end of it.

its all there just repeated multiple times

---

### Post by dave01945 on 2011-08-16
try this its an interactive shell sccipt that will guide you through the process
[www.code.google.com/p/easydvb](www.code.google.com/p/easydvb)

just download it make it executable (chmod u+x easydvb)
then run it ./easydvb

---

