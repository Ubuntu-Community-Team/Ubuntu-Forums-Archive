---
title: "Gnome + Firefox display problem"
date: 2008-07-30
forum: General Help
---

### Post by DarkAngel88 on 2008-07-30
Hi everybody,

Got this weird problem since I'm using firefox but now it's getting pretty annoying as I'm using a functionnality that has this bug.  The problem is that one of the places in firefox gets those weird color palette and it makes the form unreadable.  I attached a screenshot to illustrate this problem.

Now I know that firefox should be very customizable but I simply don't know what to do to get the background/letters the color I want.

Could anyone provide me some informations on how to change the draw section to some other colors so the panel becomes readable again !

By the way, I tested with other gnome themes but no luck, every aspect of the layout changes except this exact spot.  :(

Thank you very much !

[[IMG]http://img389.imageshack.us/img389/1110/firefoxcs6.th.jpg[/IMG]](http://img389.imageshack.us/my.php?image=firefoxcs6.jpg)

---

### Post by DJ_Peng on 2008-07-30
Have you tried different Firefox themes? Also, try it in [safe mode]("http://kb.mozillazine.org/Safe_Mode"). It seems to be a definite theming issue. I'm not quite sure why it's making that part of the theme so hard to read, but another Firefox theme may do the trick.

---

### Post by DarkAngel88 on 2008-07-30
I did not try any other firefox theme as I don't use any theme at all in this browser.  I'm pretty sure this has to do with some config in the userChrome.css or something like that but I simply can't figure it out.  Tried the safe-mode but in this mode, all the plugins are disables and I can't reproduce the desired behaviour as the plugin is unavailable.

Thanks anyway for the idea !

Anyone else has an idea on how to solve this ?

---

### Post by DJ_Peng on 2008-07-31
Actually you are using a theme in Firefox, the default theme that uses your operating system's theme/icons/color settings. You may not have seen it until Firefox 3 because the Firefox devs decided to integrate the OS theme in the default Firefox theme with this release. It may be a userChrome.css issue as well, though. If you could try another Firefox theme it could help us narrow down whether just a theme change affects it. If not, could you post the contents of your userChrome.css? We may not be as knowledgable in Firefox themes as the guys on the mozillaZine themes are, but if you post your userChrome we may be able to see a setting that's causeing this issue.

What addon are you using to get this feature? The combination of your userChrome.css and what addon you're using may help us diagnose the problem.

---

### Post by DarkAngel88 on 2008-07-31
Hi DJ_Peng,

Thanks for taking the time to answer my questions.  I have found a workaround for this issue.  My userChrome.css file was empty and I was having this issue so I digged in the extension to see if the author enforced a value for the preview panel (btw, the extension is Feeds Sidebar, pretty good if you read RSS via firefox...) and while searching, I found in a file a reference to the preview panel with the hex code "#fff" as color for the background... guess what !  I changed that value for "#000", reinstalled the extension and voilà, the preview panel is now black !!  I can read news !!

So this is a workaround as I haven't been able to fix the issue with the use of the userChrome.css file.  Anyway, problem solved for now !!  I'll continue searching for the search function because it's black now.  For example, on www,youtube.com, the searchbox is black...  This is less of an issue as it is not bothering me.

Hope it helps someone else !

---

### Post by DJ_Peng on 2008-07-31
Most excellent info, DarkAngel. I'm glad I was able to help you find a solution. I'm not sure why the search box is black. As my sig says, you may want to check out the mozillaZine Forums. They have a section specifically for theme questions so someone may be able to help resolve it for you.

---

