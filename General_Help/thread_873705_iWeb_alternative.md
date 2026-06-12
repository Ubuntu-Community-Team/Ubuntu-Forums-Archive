---
title: "iWeb alternative"
date: 2008-07-29
forum: General Help
---

### Post by ryanhaigh on 2008-07-29
I am looking for an alternative application with the same sort of simplicity and function as iWeb provides on the mac. The created site will only be stored locally and is meant to provide a unified, nicely themed, and easily modifiable method to access both locally stored and remote data. My partner was recently shown how iWeb/webpages can be used in this way and was very impressed, the problem is I have been unable to find anything similar for windows or linux (although I would prefer cross platform)

Simplicity is the key requirement here and using the same template based design system would be nice.

I know about quanta and kompozer I am looking for something even easier if possible.

[http://www.apple.com/ilife/iweb/](http://www.apple.com/ilife/iweb/)

---

### Post by cronholio on 2008-07-29
Try Aptana or Bluefish from the repositories.

---

### Post by ryanhaigh on 2008-07-29
Bluefish is not even WYSIWYG and while it might be good for the pros it is about as far from iWeb as you can get.

I can't find aptana using ubuntu package search but I am downloading the windows version (at work ATM) and will check it out.

Aptana is the same as bluefish, no wysiwyg.

---

### Post by cronholio on 2008-07-30
Well then I would say Kompozer but apparently you didn't like it. Maybe this will help: [http://en.wikipedia.org/wiki/Comparison_of_WYSIWYG_HTML_editors]("http://en.wikipedia.org/wiki/Comparison_of_WYSIWYG_HTML_editors")

---

### Post by dmizer on 2008-07-30
I'm not familiar at all with iWeb, but doesn't Open Office support this?  I know it supports wysiwyg HTML and there's probably a plugin that allows you to do more.

Edit:
Indeed ... 

File > Wizards > Web page

---

### Post by ryanhaigh on 2008-07-30
Firstly thanks for the responses thus far. Unfortunately after quite an extensive search I have still been unable to find a viable alternative to this application.

The html editors that seem popular on linux are all based on editing the html/php/etc source which is fine for web developers but not for novice users.

Kompozer isn't really up to the task, mostly due to the poor site manager feature/integration. I was looking at creating a simple starter site for her based around a couple of templates but even duplicating files isn't easily provided in this application. While you can use drag and drop for media/pdf etc files the links created use absolute paths which is just strange for a web editor and makes the feature almost useless.

The other issue is that this was never intended to be hosted on an actual webserver so without a decent app to manage all the pages and content even doing things like navigation menus becomes a huge pain as there are no server side/php includes.

OpenOffice html is ridiculous, I tried using the wizard to generate a page based on the example files provided with ubuntu and not only did the navigation etc look terrible but the content was unreadable due to images being placed over the top of text etc.

So my current options are:
[LIST]
[*]Install a light http server on her machine and use dreamweaver to do the site editing. I have a copy of this app from when I used windows and while I would personally prefer her to use something open source and cross platform there doesn't appear to be anything in the same league as far as WYSIWYG editing. If she eventually gets used to html then I will switch her over later, thats the advantage of this option its just html with SSI for the navigation at top/bottom.

[*]Install a full blown CMS on top of xampp on her pc. I don't know if this is viable as one of the most important things is to be able to link to local files. If there is a CMS that can do that and export all content to plain html then that would probably be ok.

[*]Find a desktop CMS for windows that can export to html, this is what I am looking at now as the easiest option but in the long term she will be using a non-windows os as she has no intentions of 'upgrading' to vista. I am also looking at thingamablog but there doesn't seem to be any way to use it without an actual blog (local storage only).

[*]I did look at apps that used markup to generate html such as rest2web and markdown but they aren't really beginner friendly and there didn't seem to be any decent looking sites that used them. I would be quite interested in something like this for my own needs if I could find an example of a decent modern looking site using it. If anyone could point out something like this but with an easy to use interface for linking files etc that would be great.
[/LIST]

Further suggestions on these or other options are most appreciated.

---

### Post by ryanhaigh on 2008-07-30
I have setup lighttpd on my windows vm and installed thingamablog and it seems to work quite well and I was quite happy until I realised that the beta I was released more than 6 months ago. It seems like the project may be dead?

Alternatives to this great app? Static html output is preferable.

---

### Post by dmizer on 2008-07-30
> **ryanhaigh said:**
> OpenOffice html is ridiculous, I tried using the wizard to generate a page based on the example files provided with ubuntu and not only did the navigation etc look terrible but the content was unreadable due to images being placed over the top of text etc.

That's just the wizard.

You can also just lay out your page any way you like with the Open office, then click:
File > Export

Next to "File format" select "XHTML"

Congratulations, you have a web page.

---

### Post by ryanhaigh on 2008-07-30
OpenOffice just doesn't cut it I'm afraid, word can also do html output but there is still no navigation and no media management, I need a web**site** editor . I am going to persist with thingamablog for the moment at least, until I can find a maintained alternative that has the same sort of features.

---

### Post by dmizer on 2008-07-30
Do you have any interest in Content Management Systems?  A CMS is really the closest alternative I can think of that does what you want to do.

These are clickable GUI website design interfaces which reside on your server, can be loged into from anywhere, and manipulated to your heart's content.

More information on CMS here: [http://en.wikipedia.org/wiki/Content_management_system](http://en.wikipedia.org/wiki/Content_management_system)

Here's somewhere you can test different CMS interfaces: [http://www.opensourcecms.com/index.php?option=content&task=view&id=388&Itemid=143](http://www.opensourcecms.com/index.php?option=content&task=view&id=388&Itemid=143)

Even if your site is not hosted on your own server, more often than not, one of these CMS will be available for you by your provider.

---

### Post by ryanhaigh on 2008-07-31
As mentioned above I have considered going with a full blown CMS running on XAMPP. My partner does NOT want her stuff out on the net at this stage but will need to export the site and all its associated contents (pdfs, word docs, etc) as flat files (plain html or convert content to pdf maintaining a heirachy of directories with relative links to associated media) so that it can be shared with her immediate colleagues at the school.

Thingamablog makes this relatively easy with only a couple of rough edges associated with linking files and limited flexibility in the naming of pages and directory structure.

I guess the other thing is that I want her to be able to save files within the directory structure WITHOUT using the CMS to do it. For example if she was browsing and found a really good pdf of a lesson plan for multiplication then she could just save that to a directory somewhere on her pc (i will probably make symlinks on the desktop) and it will be available for use in the CMS. Just to be clear here I don't mean it will automatically add links etc but rather that she wont then need to upload the file into the CMS system just to make a link. In short media storage should be a directory structure not a DB.

I will have a look at the CMS solutions though, I have used joomla (moodle would be better as she is a teacher) before which was relatively easy although I have to say that thingamablog is a fantastic idea allowing easy webSITE creation and management without the need for anything more than a http server for hosting. A maintained alternative to this would be preferable just for ease of use and simplicity.

---

### Post by cronholio on 2008-07-31
> In short media storage should be a directory structure not a DB.

I think most of the popular CMS out there would save a PDF file in a directory and store only the filename in the DB.

Btw, have a look at flatCMS: [http://www.flatcms.org/index.php]("http://www.flatcms.org/index.php"). It's a basic CMS that doesn't rely on a DB and I found it to be useful many times.

---

### Post by Exodist on 2009-08-08
I noticed  you didnt like Kompozer, shame its not bad for a WYSIWYG editer. Mind you it still falls far behind DreamWeaver and even old Frontpage. But as far as creating sites, its not a high end software but it can do lots. The biggest drawback is getting used to  it.
I recomend trying it for a week. I used NVu for a long while and Kompozer has little more stylesheet intigration.

Other option would to find a older copy of Macromedia (now Adobe) Dreamweaver and run it with Wine.

So for WYSIWYG editor that are native linux, go Kompozer.
Or take a chance and trying FP or DW under Wine, wich stability could be a concern. Save webpage frequently..
Last, learn HTML.. If your like me another programming laungauge to learn will only lead to bleeding from my ears.. :-)

Cheers,
Exo

---

### Post by AnarchyLinux on 2009-11-09
**Ever tried UWEB? as a alternative to IWEB?**

---

