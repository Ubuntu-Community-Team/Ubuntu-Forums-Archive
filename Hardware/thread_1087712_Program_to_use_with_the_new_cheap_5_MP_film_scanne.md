---
title: "Program to use with the new cheap 5 MP film scanners?"
date: 2009-03-05
forum: Hardware
---

### Post by radi0j0hn on 2009-03-05
There are a whole bunch of new film/slide "scanners" that are actually fixed focus 5 MP cameras in a box with an LED light stage under them.  They are USB powered and have no moving parts aside from the negative/slide mount. Despite various names (VuePoint, etc.) they all appear the same on the inside.  Priced from about $69 - $99. 

Has anyone figured out what program works with these units, as there only appears to be Windows software?

And yes, I know they are not as good as a real film scanner.

---

### Post by TheropodWatcher on 2009-08-09
@radiOjOhn - check with Amazon and a few other places. Some of these things actually scan to a SanDisk card, which you can then plug into a card reader attached to your computer. Here's one on Amazon: [http://www.amazon.com/Imagelab-FS5CO5-Megapixel-Negative-Scanner/dp/B001TDL2BI/ref=sr_1_2?ie=UTF8&qid=1249864755&sr=8-2](http://www.amazon.com/Imagelab-FS5CO5-Megapixel-Negative-Scanner/dp/B001TDL2BI/ref=sr_1_2?ie=UTF8&qid=1249864755&sr=8-2)
 If you decide to go with a "real" scanner, check out the commercial software called VueScan. [http://www.hamrick.com/](http://www.hamrick.com/) $40 download and excellent. It solved my scanning issues just about the time I was ready to give up. (I have no relationship with either product other than finding them while trying to get scanning to work on my Linux box.)

---

### Post by remer on 2012-12-08
Dear all,
I just bought a MEDION E89000 (MD 86601) USB Scanner for slides and negatives.
Using Microsoft Seven 64 bits, it appears as **USB Scanner 5MP**.
I'm actually running **Ubuntu 12.04.1 LTS**.
If I type :```
$ lsusb
```
I get this : ```
Bus 001 Device 009: ID 115b:3150 Salix Technology Co., Ltd. 

```
Till now, this scanner appears as a webcam. Using [Studio Webcam Cheese]("http://projects.gnome.org/cheese/"), I've been able to record an image and then I've used [Gimp]("http://www.gimp.org/") in order to invert colors.
... a bit complicated. If you have a simplier solution, I'm interested.

---

### Post by cainn on 2012-12-16
> **remer said:**
> Till now, this scanner appears as a webcam. Using [Studio Webcam Cheese]("http://projects.gnome.org/cheese/"), I've been able to record an image and then I've used [Gimp]("http://www.gimp.org/") in order to invert colors.
... a bit complicated. If you have a simplier solution, I'm interested.

Great tip remer.  Cheese also works with the Digitech XC4881 Negative Film/Slide Scanner sold by Jaycar in Australia.  In fact I can get superior results (in terms of colour reproduction) working directly with the negative (captured by Cheese) in Gimp than I do working with the output of the Windows software that came with the device.  Most of the time, Colors > Invert, followed by Colors > Auto > White Balance produces good results, which can then be further tweaked according to preference.

The main reason I'm posting here is so this thread comes up in a google search on "XC4881 ubuntu", as I didn't find it until I searched on the output of lsusb.

"sudo apt-get install cheese" folks ;)

Thanks!

---

### Post by Antony_F_Heaton on 2013-09-21
I bought a similar, cheap scanner from Aldi in UK and I found that cheese/gimp was a workable solution. However, for colour negatives I installed "gnome-video-effects-frei0r" and this gave me, among other additional effects, "invertion" (sic), which reverses the colours within the cheese preview and allows direct saving of the positive image. There is a slight blue cast to the images, but the detail is much better than I get from the Windows software included with the scanner - this gives a better colour balance, but the highlights are oversaturated and detail is lost.

I hope this is the simpler solution you were looking for: I am certainly pleased with the speed and ease of the process when I use "invertion", and I use this in preference to the supplied Windows software.

---

### Post by gmu2 on 2014-06-10
Hello to all,

I'm a very new ubuntu user with a little hardware problem. But I'm sure, that someone of you can help me ;-)
Before I start to describe my problem, please excuse me for my English, but it's not my native language and sorry for any mistakes!

I got also a photo scanner (producer or charger is the German Medion AG) described above. When I plug it to my usb port, I got a new entry for the **lsusb** command:
[FONT=courier new]Bus 001 Device 006: ID 115b:3150 Salix Technology Co., Ltd.[/FONT]

So firstly I'm very happy to found this thread for a solution to use this scanner and followed the steps from the other posts. I installed cheese with the following steps:
[FONT=courier new]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install cheese
[/FONT]
I got the following result (in German):
[FONT=courier new]cheese ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 3 nicht aktualisiert.
[/FONT]
This means cheese is already the latest and nothing has to change (so long so good).
When I start **cheese** (with my normal user) I got the following messages:
[FONT=courier new]libGL error: failed to open drm device: Datei oder Verzeichnis nicht gefunden
libGL error: failed to load driver: vboxvideo
** Message: cheese-application.vala:291: Error during camera setup: Kein Gerät gefunden


(cheese:7716): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:7716): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(cheese:7716): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:7716): GLib-CRITICAL **: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:7716): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:7716): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed
[/FONT]

The program window from cheese starts with the message "Ein Fehler ist beim Abspielen des Videosignals von der Webcam aufgetreten". If I call Cheese Info I got the program version 3.10.2 (and I use Ubuntu 14.04 LTS). Now I have no idea to fix the problem, but some questions:
1. In the first (error) line the program said [FONT=courier new]open drm device: file or directory not[/FONT] [FONT=courier new]found[/FONT]. What does it mean? What are the steps I have to do?
2. Does the second [FONT=courier new]libGL error: failed to load driver: vboxvideo[/FONT] has anything to do with my local running VM-Ware instance? Is this error only occurs because Ubuntu isn't running on a real hardware? I use this vm for testing because I don't have any idea to revert some wrong installations or steps on the real desktop.
3. The cheese error [FONT=courier new]Error during camera setup: Kein Gerät gefunden[/FONT] (no device found) doesn't help me. Which steps are neccessary to enable the device (found by the lsusb command)?

Many many thanks in advance for any help or ideas to enable this device for me.
Best regards,
gmu

---

