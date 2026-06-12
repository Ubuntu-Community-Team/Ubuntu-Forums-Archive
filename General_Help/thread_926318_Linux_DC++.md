---
title: "Linux DC++"
date: 2008-09-21
forum: General Help
---

### Post by Brando569 on 2008-09-21
Hey I'm trying to do the same thing as [This User](http://ubuntuforums.org/showthread.php?t=760269&highlight=ruxan) but I dont know if the patch worked correctly since there wasnt any output. I navigated to the directory of linuxdcpp, applied the patch with patch -p0 < ruxan.patch, then ran scons to compile it. 

Everything compiled successfully yet I still cant connect to the hub :( this is really annoying considering that most people on the hub wont help you with anything, ive tried asking before and I get the typical a$$hole responses such as "who cares its the end of the semester"

---

### Post by TwistableLime on 2008-09-21
What where the steps you took to patch linuxdcpp? I'm not sure which file to patch and not sure what to do when you speak of scons. 

Thanks.

---

### Post by Brando569 on 2008-09-22
i extracted the tar ball and placed the patch in the main directory of it and executed 

patch -p0 < ruxan.patch 

and it just brought me back to my bash prompt, i tried placing the patch in the linux directory and patched it again with the same results. scons is a program that will configure and compile the program. it takes the place of ./configure and make.

---

### Post by TwistableLime on 2008-09-22
Every time I used the "patch -p0 < filename.patch" command I was presented with error messages at 2 specific lines, it then asked me which file I would like to patch and I wasn't which file it was. However whichever file I tried seemed to fail. I think the two files I tried were DC++.xml and LinuxDCPP.xml (those file names may be different as I'm not on my linux computer).

---

### Post by Brando569 on 2008-09-22
what are the errors youre getting? i didnt get any output at all

from reading the patch i can tell that we need [version 1.0.0](http://prdownload.berlios.de/linuxdcpp/linuxdcpp-1.0.0.tar.bz2) of linuxdcpp and the files that it is trying to patch are linuxdcpp-1.0.0/client/NmdcHub.cpp and linuxdcpp-1.0.0/client/version.h 

i examined the file a little more and this is what i found:

the patch adds this into nmdchub.cpp:	">$ $LAN(T3)\x01$" + fromUtf8(escape(SETTING(EMAIL))) + '$'; 
and deletes this from nmdchub.cpp (?):	">$ $" + SETTING(UPLOAD_SPEED) + "\x01$" + fromUtf8(escape(SETTING(EMAIL))) + '$';

and the patch changes this in version.h:
#define VERSIONSTRING "0.698" to #define VERSIONSTRING "0.674"
#define VERSIONFLOAT "0.698" to #define VERSIONFLOAT "0.674"

im going to try the patch again and if it doesnt work im going to try and change it manually then compile it

---

### Post by Brando569 on 2008-10-04
I finally got it to work, go download [Valknut and DcLib](http://sourceforge.net/project/showfiles.php?group_id=181579) and compile and install them. execute valknut and in the settings change the upload slots to the normal 3, share whatever you want, and change your connection mode to active and do it by interface and select eth0

mine kept on telling me that i had invalid settings, then it would tell me i didnt have enough slots open and that i had invalid settings, then it would tell me i had invalid settings and kick me off, then it retried and im on.

edit:

i was talking about this in the chat and the guy that made the patch messaged me and told me that there was a new version and told me how to do everything. heres what i did:

1.downloaded version 1.0.2 and extracted it
2.applied the new patch with sudo patch **-p1** < linuxdcpp-1.0.2-ruxan.patch
3.compiled it with the command "scons" (no quotes)
4.then sudo scons install
5.run linuxdcpp :D

heres the new patch
```
diff -ur linuxdcpp-1.0.2/client/NmdcHub.cpp patched/linuxdcpp-1.0.2/client/NmdcHub.cpp
--- linuxdcpp-1.0.2/client/NmdcHub.cpp	2008-07-02 23:54:12.000000000 -0400
+++ patched/linuxdcpp-1.0.2/client/NmdcHub.cpp	2008-08-31 20:02:46.000000000 -0400
@@ -800,7 +800,7 @@
 	string myInfoA =
 		"$MyINFO $ALL " + fromUtf8(getMyNick()) + " " + fromUtf8(escape(getCurrentDescription())) +
 		tmp1 + VERSIONSTRING + tmp2 + modeChar + tmp3 + getCounts() + tmp4 + Util::toString(SETTING(SLOTS)) + uMin +
-		">$ $" + SETTING(UPLOAD_SPEED) + "\x01$" + fromUtf8(escape(SETTING(EMAIL))) + '$';
+		">$ $LAN(T3)\x01$" + fromUtf8(escape(SETTING(EMAIL))) + '$';
 	string myInfoB = ShareManager::getInstance()->getShareSizeString() + "$|";
  
  	if(lastMyInfoA != myInfoA || alwaysSend || (lastMyInfoB != myInfoB && lastUpdate + 15*60*1000 < GET_TICK()) ){
diff -ur linuxdcpp-1.0.2/client/ShareManager.h patched/linuxdcpp-1.0.2/client/ShareManager.h
--- linuxdcpp-1.0.2/client/ShareManager.h	2008-05-04 14:55:25.000000000 -0400
+++ patched/linuxdcpp-1.0.2/client/ShareManager.h	2008-08-31 20:05:10.000000000 -0400
@@ -39,6 +39,8 @@
 
 #include <memory>
 
+#include <memory>
+
 STANDARD_EXCEPTION(ShareException);
 
 class SimpleXML;
diff -ur linuxdcpp-1.0.2/client/version.h patched/linuxdcpp-1.0.2/client/version.h
--- linuxdcpp-1.0.2/client/version.h	2008-05-27 02:56:56.000000000 -0400
+++ patched/linuxdcpp-1.0.2/client/version.h	2008-08-31 20:03:54.000000000 -0400
@@ -16,8 +16,8 @@
  * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
  */
 
-#define APPNAME "LinuxDC++"
-#define VERSIONSTRING "0.698"
-#define VERSIONFLOAT 0.698
+#define APPNAME "DC++"
+#define VERSIONSTRING "0.674"
+#define VERSIONFLOAT 0.674
 
 /* Update the .rc file as well... */
```

---

### Post by stevensheehy on 2008-10-12
Hmmm....let me guess. It's probably an OpenDC hub v0.7.1.4? If so, you could've just changed your upload speed to 5 and it would let you in. If they have an additional check on version <= 0.674 then you would still need to modify the code though.

---

### Post by Brando569 on 2008-10-13
yep

> <Hub-Security> This hub is running version 0.7.14 of Open DC Hub.

good to know

---

