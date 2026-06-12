---
title: "How do I create a &quot;dynamic&quot; login background?"
date: 2008-09-20
forum: General Help
---

### Post by zergnerd on 2008-09-20
I recently got Ubuntu Hardy and modified a downloaded theme to use my own background on the login screen.  I would like to be able to randomly pick from a short list of backgrounds and have a different login screen background each time I login.  

My initial thought was to modify the GDM....desktop file and put an awk or sed command to replace a $CUSTOMBKGND flag in the .xml file with the name of a file.  I would then save it under a different name and point the Greeter= line to the new .xml file.  Since I have to give the login manager a tar.gz package, this won't work.  How do I run a different login background each time I log in?

The text in aurora-theme.xml I want to replace:
```
<!-- Background-->
<item type="svg">
	<normal file="$CUSTOMBKGND"/>
	<pos x="0" y="0" width="100%" height="100%"/>
</item>
```

$CUSTOMBKGND should randomly become file1.jpg - file10.jpg

The current contents of the GDMGreeterTheme.desktop file
```
[GdmGreeterTheme]
Encoding=UTF-8
Greeter=aurora-theme.xml
Name=Hicks GDM v0.4
Description=ZergNerd's GDM Theme
Screenshot=screenshot.png
```

Thanks for your all your help.

---

### Post by Genius314 on 2008-09-20
Well, you could make a bunch of GDM themes, each with a different background.
Then, you go to System>Admin>Login Window, in the Local tab. For the "Theme" drop down box, select "Random from Selected." Now just check each box next to the themes that you made.

---

### Post by steveneddy on 2008-09-20
Sounds like this is solved.

---

