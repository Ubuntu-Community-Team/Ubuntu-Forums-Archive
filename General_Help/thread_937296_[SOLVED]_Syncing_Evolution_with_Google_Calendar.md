---
title: "[SOLVED] Syncing Evolution with Google Calendar"
date: 2008-10-03
forum: General Help
---

### Post by MaverickCoast on 2008-10-03
I've been looking for good instructions to do this and want to share how I found to do it step-by-step. 

I am using Evolution 2.22.3.1.

[COLOR="Red"]Disclaimer:[/COLOR]
[COLOR="Red"]This will NOT allow you to transfer entries FROM your Evolution Calendar to your Google Calendar . It will only allow Evolution to "download" what is on your Google Calendar to your Evolution calendar.[/COLOR]
I STILL find it useful if the wife enters something onto the Google Calendar when she is somewhere else. This way I can keep our other family calendars up-to-date on our other PCs!

Enjoy....

- Goto your Google Calendar
- Goto "Settings" (Upper right)
- Underneath "Calendar Settings", click on "Calendar"
- Click on the name you've given your calendar
- Scroll to bottom and look for "Private Address"
- Click on "ICAL" next to "Private Address"
- In pop-up window, you'll see the address of your calendar.
- Copy all of the address [COLOR="Red"]_**BUT**_[/COLOR] the "http://" (Start with "www")
- Click "OK"

- Open Evolution
- Bottom left, click on "Calendar"
- Top left, click on arrow next to "New"
- In drop down menu, click on "Calendar"
- "New Calendar" window will open
- Next to "Type", select "On The Web"
- Name your new calendar
- Choose color
- Select next two options (boxes), if you want.
- Next to "URL" and [COLOR="Red"]after[/COLOR] "webcal://", paste in your Google Calendar address (that starts with "www")
- Leave "Secure Connection" UNCHECKED
- Next to "Username", enter the username you use to login to your Google Calendar ([COLOR="Red"]Only enter the first part[/COLOR], don't enter @xxxx.xxx)
- Select the refresh rate at the bottom.
- Click "OK"

- You will be asked for your password that you use to access your Google Calendar. After you enter it, your Evolution Calendar will reflect your Google Calendar. [COLOR="Red"]NOTE:[/COLOR] If you click on "Remember Password", the next time it asks for your password, just click on "OK", even though nothing shows in the entry window.


:guitar:

...Sorry if this is a repeat post, but after doing numerous searches I couldn't find any clear instructions on how to sync Evolution with Google Calendar.

---

### Post by nwillettjeffries on 2008-10-28
Thanks for this guide as I haven't been able to find anything else that offers nearly as clear directions as you do.

Having said that I still wasn't able to replicate your success...
I followed all the directions exactly and when I clicked ok on the new calendar dialog in evolution nothing happened. I was not prompted for a password or anything and evolution never updated with the contents of my google calendar. I checked my evolution version and it's 2.22.3.1 just as the directions state. Any ideas what I could be doing wrong? Is anyone else having a similar problem?

---

