---
title: "[SOLVED] how do I change default email client"
date: 2008-09-25
forum: General Help
---

### Post by charonred on 2008-09-25
I use Firefox for my browser (of course), but don't like Evolution as the email client (too clunky)

When I'm browsing the web, and I click on a email link, I want Thunderbird to handle the email, not Evolution. How do I change the default email client to Thunderbird; I see in Firefox 'edit>preferences>applications>mailto' that I can select 'Use Other', but what application file do I actually select in order to launch a new Thunderbird email?

---

### Post by iaculallad on 2008-09-25
System->Preferences->Preferred Applications
On the “Internet” tab, simply select “Thunderbird” from the drop down menu. If it is not present then Select “Custom” and type in the command box “thunderbird %s” (that's without quotes)

---

### Post by charonred on 2008-09-25
thanks for prompt reply; but there is no 'preferred applications' in FF3, only 'applications' tab, which has a list of 'content type' and 'action'

'action' for 'mailto'(content) is a drop-down list of ;
Evolution
Yahoo
Gmail
Use other

'Use other' provides a 'browse to' window - what do I browse to and which particular file do I choose (there doesn't appear to be an option to place the script you provided)

---

### Post by iaculallad on 2008-09-25
Ahh, I thought you're asking for the default application setting. Try:

In Firefox’s Location/Address Bar, type **about:config** and hit Enter key.
Right-click on the body. From the pop-up menu, select 'New' -> 'String' and in the pop-up dialog box “Enter the preference name”, enter
**network.protocol-handler.app.mailto**
and click “OK” button.

In the pop-up dialog box 'network.protocol-handler.app.mailto', enter **/usr/bin/thunderbird** as it's value then click on 'OK'

---

### Post by TeXtonyx on 2008-09-25
I just solved this problem. First,
System->Preferences->Preferred Applications
On the “Internet” tab, simply select “Thunderbird” from the drop down menu

Then when you go back to FF, applications, mailto, Thunderbird will have
been added to the dropdown list of email clients to choose from.

---

### Post by charonred on 2008-09-25
thanks iaculallad; it now shows Thunderbird in the 'mailto' options, but when I click on an email link, it still opens a new Evolution compose email window (even after re-starting FF3).

---

### Post by iaculallad on 2008-09-25
Try performing the steps in my first post. Only this time, you have to configure your preferred applications.

---

### Post by charonred on 2008-09-25
sorry, but that option just doesn't exist - see attachment for image of preferences window

---

### Post by iaculallad on 2008-09-25
> **charonred said:**
> sorry, but that option just doesn't exist - see attachment for image of preferences window

No, that process was not meant to be performed in FF window. Go directly to System->Preferences->Preferred Application (On your uppermost taskbar).

---

### Post by charonred on 2008-09-26
ah ha, that fixed it - I didn't see the 'system' bit....DOH
and Thunderbird was in there as an option - brilliant :)

many thanks

---

### Post by saxonjf on 2008-10-01
Thanks for the help.  Once I knew that the program could be found under

/usr/bin/thunderbird, I chose that file when I chose other, after clicking on it.  Now when I click on the link, thunderbird outgoing email box pops right up.

Thanks for the help

---

