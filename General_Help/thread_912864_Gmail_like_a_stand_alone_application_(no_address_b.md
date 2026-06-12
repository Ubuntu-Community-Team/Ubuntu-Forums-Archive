---
title: "Gmail like a stand alone application (no address bar etc.!)"
date: 2008-09-07
forum: General Help
---

### Post by mercmobily on 2008-09-07
Hi,

I'd like to run Gmail so that it looks like a stand alone application.
I guess all I need is a Firefox command so that I tell it, in the parameters, to just open gmail and display no address bar, no bookmarks... nothing.

What's the easiest way to do this?

Bye!

Merc.

---

### Post by Paul41 on 2008-09-07
This is exactly what Mozilla's Prism does. I have not used it so I can't comment on how good it works and it is still in development but may be worth a try since it does exactly what you are looking for.

[http://labs.mozilla.com/2007/10/prism/](http://labs.mozilla.com/2007/10/prism/)

---

### Post by Ms_Angel_D on 2008-09-07
I use Prism All the time it works fantastic! I also use it for google docs and google calendar. It's available in the Add/Remove Programs.

---

### Post by lovinglinux on 2008-09-07
I also use Prism for several things. The only downside is that you can't use Firefox extensions (at least I don't know how). I miss security extensions and cool things like Stylish. But if you don't go outside Google using Prism you should be safe.

---

### Post by dorkdork777 on 2008-09-07
Exactly how to get it on Ubuntu 8.04:
[list=1][*]Click Applications, then Add/Remove.[*]Set the drop-down next to 'Show' to 'All available applications'.[*]In the search box, type "gmail prism". [*]Click the checkbox on the left-hand side of the one application listed here.[*]Click "apply changes", then "Apply".[*]Enter your password, click 'Apply' once more if necessary.[/list]

---

### Post by fragos on 2008-09-07
Gmail supports POP and IMAP. You can use Evolution or any other mail package as your client. It even works with the email client in my Nokia N810.

---

### Post by snowpine on 2008-09-07
> **mercmobily said:**
> Hi,

I'd like to run Gmail so that it looks like a stand alone application.
I guess all I need is a Firefox command so that I tell it, in the parameters, to just open gmail and display no address bar, no bookmarks... nothing.

What's the easiest way to do this?

Bye!

Merc.

Press F11 :)

---

### Post by Vivaldi Gloria on 2008-09-07
I also suggest prism. To set it up see my posts [[COLOR="DarkOliveGreen"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=857396").

---

### Post by mercmobily on 2008-09-17
Hi,

THANK YOU everybody.
Shame on me, I should have known about it... I even edited an article for Free Software Magazine about this!

:-D

Thanks,

Merc.

---

### Post by mercmobily on 2008-09-17
Hi,

THANK YOU everybody.
Shame on me, I should have known about it... I even edited an article for Free Software Magazine about this!

:-D

Thanks,

Merc.

---

### Post by Lightbreeze on 2008-10-06
Hey, I use Gmail in a Prism window to compose messages.
Because I don't use the prism-gmail package, I have a bash script I made to handle all those little mailto: links. So To, Subject, And Body text should all work well.

It's attached in case anybody finds it helpful.
[LIST=1]
[*]First you need Mozilla Prism
[*]Then you need to open prism and create an app called "compose mail" (put in any other imformation the the boxes you feel like.).
[*]Save the compose-gmail.sh attachment somewhere and make it executable (right click > Properties> then 'Permissions' tab)
[*]In the Ubuntu main menu go System > Preferences > Preferred Applications and under Email go 'Custom' and enter the path to the script file. e.g */home/username/Templates/compose-gmail.sh %s* the %s is important: it passes the email addresses to the script.
[/LIST]

Hope it helps someone else. I love it 'cause now I can use GNOME-Do to email to my hearts content :)

---

### Post by Sonja on 2008-10-06
When I click on a mailto link in my browser, it doesn't seem to launch and send with Prism Gmail. Do you think I missed a step?

Is the creation of the web app supposed to leave a link on the desktop?

---

### Post by Lightbreeze on 2008-10-07
Yeah, check the box to have a shortcut on your desktop. But you can delete that later.

Check that there is a folder called *~/WebApps/compose.mail@prism.app*. Check that you have the script executable and that in the Preffered Apps it points to that script with the *%s* sign after it.
I'm using Prism 0.9.. I guess there could be mishaps with older versions..

Hope this helps - keep posting if it doesn't

---

### Post by crysys on 2008-11-11
I'm having trouble getting mailto links working with prism.  I tried a few different configurations including Lightbreezes' script.  That one didn't work for me at all unfortunately. I'm currently using the prism-google-mail app and I also tried it with an alternate webapp.js file from skrul.com.

I have a prism-google-mail option in the application list in FF3 but clicking mailto links only launches my inbox in prism.  I'm guessing the mailto link is not triggering the launch of a compose window but I don't know if there is an error or if the functionality just doesn't exist in the webapp.

I've included the webapp.js from skrul, if anyone is able to help me out it would be appreciated.

---

### Post by Lightbreeze on 2008-11-11
Sorry crysys I had a look at webapp.js.txt but I didnt really get it.. I'll have a better look later.
If you want to try my script again the only thing I can think of is making sure the script is executable, that %s is in the mailto in preffered apps, and that the name of the webapp is the same as in my script (~/WebApps/compose.mail@prism.app).

I don't know javascript... maybe you should have that script exeuctable as well? and maybe take of the .txt at the end?

Yeah and I guess just check the firefox preferences > applications > mailto:

---

### Post by warp4ever on 2010-01-10
Reading your post it is not clear to me what the parameters need to be :

"2.Then you need to open prism and create an app called "compose mail" (put in any other imformation the the boxes you feel like.)."

I can't leave them empty if I feel like it, can I ? 

Do I need to "about:config" Firefox's mailto handler?

Can you give a more explicit direction to the whole procedure?
I do not want to follow the "how-to-geek" since his script forces me to use Firefox instead of a already present Prism Gmail app.

---

### Post by warp4ever on 2010-01-10
BTW I do use the prism-gmail package.

---

### Post by Colin Keenan on 2011-02-17
> **Lightbreeze said:**
> Hey, I use Gmail in a Prism window to compose messages.
Because I don't use the prism-gmail package, I have a bash script I made to handle all those little mailto: links. So To, Subject, And Body text should all work well.

It's attached in case anybody finds it helpful.
[LIST=1]
[*]First you need Mozilla Prism
[*]Then you need to open prism and create an app called "compose mail" (put in any other imformation the the boxes you feel like.).
[*]Save the compose-gmail.sh attachment somewhere and make it executable (right click > Properties> then 'Permissions' tab)
[*]In the Ubuntu main menu go System > Preferences > Preferred Applications and under Email go 'Custom' and enter the path to the script file. e.g */home/username/Templates/compose-gmail.sh %s* the %s is important: it passes the email addresses to the script.
[/LIST]

Hope it helps someone else. I love it 'cause now I can use GNOME-Do to email to my hearts content :)

The compose-gmail.sh file linked to in the quote above has some problems and doesn't work in general.  After working on it a while, I came up with the following simplified version that works for me:

TOMAIL=`echo $1 | sed 's/mailto://' | sed 's/?subject=/\&su=/g' `

TOURL="https://mail.google.com/mail?view=cm&tf=0&to="

echo "[Parameters]
id=compose.mail@prism.app
name=Compose Mail
uri=$TOURL${TOMAIL}
icon=webapp
status=false
location=false
sidebar=false
navigation=false
trayicon=false" > /home/colin/.webapps/compose.mail@prism.app/webapp.ini

prism -override "/home/colin/.webapps/compose.mail@prism.app/override.ini" -webapp [email]compose.mail@prism.app[/email]


To make it work for you, just replace both instances of "/home/colin" with your home name.  In step 2, leave everything blank except fill in the name "compose.mail" and checkmark to put the icon on your desktop.  Delete that icon after creating it.  The reason you can leave everything blank is that the script fills in the blanks each time it runs - that's how it's able to open a different web location each time to include all the information in the email link you are clicking on.

Along the way, I had also upgraded to the beta version of prism, but that may not be necessary.  Here is a link to the prism wiki where you can get the beta version: [https://wiki.mozilla.org/Prism](https://wiki.mozilla.org/Prism)

---

