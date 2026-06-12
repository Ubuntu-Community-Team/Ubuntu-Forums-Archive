---
title: "Empathy and Telepathy-haze"
date: 2008-11-07
forum: General Help
---

### Post by hanzomon4 on 2008-11-07
I'm trying to get myspaceIM and facebook chat working in empathy via telepathy-haze. Telepathy-haze allows you to use all of the protocols supported by libpurple(pidgin). 

Running  HAZE_PERSIST=1 HAZE_DEBUG=all /usr/lib/telepathy/telepathy-haze returns a list of protocols found by telepathy-haze ```
 DEBUG: get_protocols: Found protocols aim, **[color=red]bigbrownchunx-facebookim[/color]**, gadugadu, groupwise, icq, irc, jabber, local-xmpp, msn, **[color=red]myspace[/color]**, qq, sametime, silc, simple, yahoo, zephyr
``` 

As you can see myspace and facebook are listed, however in the empathy account window I don't see the option to create a facebook or myspace account. 

I checked  /usr/share/telepathy/managers/ and saw a bunch of *.glade for everyone of the protocols in the account setup window, myspaceIM and facebook IM were missing which I guess explains why it doesn't show up in the empathy account setup window.

Does anyone know how to this up? Telepathy-haze does pickup all of the pidgin protocols I just can't seem to find a way to set them up in empathy.

---

### Post by hanzomon4 on 2008-11-07
No one?

---

### Post by loell on 2008-11-07
you better ask at [telepathy mailing list]("http://lists.freedesktop.org/mailman/listinfo/telepathy")

---

### Post by dasunst3r on 2008-11-26
I just got it working.  Have a look at this: [https://bugs.freedesktop.org/show_bug.cgi?id=17907](https://bugs.freedesktop.org/show_bug.cgi?id=17907)

haze.manager can be found at /usr/share/telepathy/managers
Create bigbrownchunx-facebookim-haze.profile at /usr/share/mission-control/profiles

This works for the latest version of the plugin (1.38).

---

### Post by tich on 2008-12-01
> **dasunst3r said:**
> I just got it working.  Have a look at this: [https://bugs.freedesktop.org/show_bug.cgi?id=17907](https://bugs.freedesktop.org/show_bug.cgi?id=17907)

haze.manager can be found at /usr/share/telepathy/managers
Create bigbrownchunx-facebookim-haze.profile at /usr/share/mission-control/profiles

This works for the latest version of the plugin (1.38).


I checked out the website but I was wondering if you could give step-by-step instructions for getting facebook chat working.

It looks pretty straight forward but it is just vague enough that i could screw it up.

thanks!

---

### Post by tich on 2008-12-01
actually it was less vague than i thought.

thanks for the post.
do you know where the icons are supposed to go?
and what should they be renamed to?

---

### Post by dasunst3r on 2008-12-04
Unfortunately, I do not know where the icons are placed.

---

### Post by suoko on 2008-12-14
terminal solution:

wget [https://bugs.freedesktop.org/attachment.cgi?id=20810](https://bugs.freedesktop.org/attachment.cgi?id=20810)
sudo mv attachment.cgi?id=20810 /usr/share/telepathy/managers/haze.manager
wget [https://bugs.freedesktop.org/attachment.cgi?id=20811](https://bugs.freedesktop.org/attachment.cgi?id=20811)
sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile

---

### Post by fr500 on 2009-01-06
> **tich said:**
> actually it was less vague than i thought.

thanks for the post.
do you know where the icons are supposed to go?
and what should they be renamed to?

Great it works! icons are at /usr/share/empathy/hicolor..... and according to the profile you created, facebook.png will do fine.

Cheers!

---

### Post by hanzomon4 on 2009-01-17
YaY!!!

How do I set this to solved

---

### Post by edog76 on 2009-01-23
top of the thread, thread tools

---

### Post by philliptweedie on 2009-05-17
Sorry for the bump but I thought it best to keep this under one thread. The method described below always results in a network error for me. Anyone else still able to get this method to work?

> **suoko said:**
> terminal solution:

wget [https://bugs.freedesktop.org/attachment.cgi?id=20810](https://bugs.freedesktop.org/attachment.cgi?id=20810)
sudo mv attachment.cgi?id=20810 /usr/share/telepathy/managers/haze.manager
wget [https://bugs.freedesktop.org/attachment.cgi?id=20811](https://bugs.freedesktop.org/attachment.cgi?id=20811)
sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile

Any help would be appreciated.

Cheers

UPDATE : Disregard all of the above, almost immediately got it to work once I posted this message.

Thanks anyway!

---

### Post by psychok7 on 2009-09-10
> **suoko said:**
> terminal solution:

wget [https://bugs.freedesktop.org/attachment.cgi?id=20810](https://bugs.freedesktop.org/attachment.cgi?id=20810)
sudo mv attachment.cgi?id=20810 /usr/share/telepathy/managers/haze.manager
wget [https://bugs.freedesktop.org/attachment.cgi?id=20811](https://bugs.freedesktop.org/attachment.cgi?id=20811)
sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile

hi.. i tried your insctructions but i guess this error in the last command "mv: cannot move `attachment.cgi?id=20811' to `/usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile': No such file or directory"

im using jauny, with an additional repository so now im using the latest empathy.how do i correct this?

---

### Post by Kapitän Rotbart on 2009-09-17
Shucks, using Jaunty, got the same problem as psychok7. However I manually created the /usr/share/mission-control/profiles/ directory, and I added the account to Empathy however it won’t connect. Under "Advanced" I see "Server" (default is blank) and "Facebook_hide_self" (default is "0").

I also figured the same as Nephi513 and didn’t bother downloading it from the Google Code page as I already had it installed from the repos.

Any solution to this?

---

### Post by Locke_99GS on 2009-09-20
Same results here on Karmic.

Does anyone have the server information for Facebook?

---

### Post by Kapitän Rotbart on 2009-10-02
Bump!

---

### Post by bobpaul on 2009-10-03
There is no longer a /usr/share/mission-control folder, so we can't place the profile file until the new location is found. Perhaps someone knows what happened to mission-control?

To help others figure it out, the attachments listed earlier are part of this bug report, comments 3 and 4:
[https://bugs.freedesktop.org/show_bug.cgi?id=17907](https://bugs.freedesktop.org/show_bug.cgi?id=17907)

**[Edit]** More info may be found here: [http://telepathy.freedesktop.org/wiki/Haze%20FAQ](http://telepathy.freedesktop.org/wiki/Haze%20FAQ)

Karmic uses mission-control 5. It would see that getting facebook chat working in Karmic should require installing the pidgin-facebookchat package and then deleting /usr/share/telepathy/managers/haze.manager. Unfortunately, I still can't get it to connect.

---

### Post by bekind2thenoob on 2009-10-04
> **bobpaul said:**
> Karmic uses mission-control 5. It would see that getting facebook chat working in Karmic should require installing the pidgin-facebookchat package and then deleting /usr/share/telepathy/managers/haze.manager. Unfortunately, I still can't get it to connect.

This method works for me.

I'm using a fresh install of Karmic beta 64 bit and the latest pidgin-facebookchat (1.61) from their google code site.

[http://code.google.com/p/pidgin-facebookchat/]("http://code.google.com/p/pidgin-facebookchat/")

---

### Post by Kapitän Rotbart on 2009-10-04
I followed the instructions [from this post]("http://www.callum-macdonald.com/2009/09/21/ubuntu-jaunty-and-pidgin-facebookchat-1-61/") in order to install the latest version of pidgin-facebookchat DEB package (from its google code page). I got the dependency installed, installed the deb for pidgin-facebookchat, deleted haze.manager, Facebook-Chat appears in the list for Empathy, I can do anything except for connecting! Will this feature ever work in Jaunty? I know Karmic is only weeks away, but I am not going to run the beta just to hope that "tweaking around" would be simpler.

---

### Post by Kapitän Rotbart on 2009-10-07
Bump.

---

### Post by hanzomon4 on 2009-10-10
On Karmic after deleting the haze.manager rebooting got it to connect

---

### Post by lolwhites on 2009-10-29
Have tried installing pidgin-facebookchat and deleting haze-manager in Karmic. Facebook-Chat appears in the list but won't connect.

---

### Post by lingnoi on 2009-11-05
I got it working on karmic by installing the latest facebook deb from the google code project site and then I placed the bigbrownchunx-facebookim-haze.profile file in my user directory..

./mission-control/profiles/bigbrownchunx-facebookim-haze.profile

I also installed the haze.manager in the location previously specified.

---

### Post by psychok7 on 2009-11-05
works for me to..i installed the facebook plugin, and after retrying the first methods and not working , i deleted haze.manager, and i can now connect

---

### Post by HarshReality on 2009-11-06
Same here but it isnt showing the groups :/ 500+ contacts in FB makes that a bit more than messy.

---

### Post by Joshisfloyd on 2010-02-28
If anyone stumbles across this page, I would like to point out that none of this is necessary anymore. Facebook chat now supports XMPP/Jabber. You simply add an existing account in Empathy, with your [email]username@chat.facebook.com[/email]. For more information see the link.

[http://lifehacker.com/5469583/how-to-add-facebook-chat-to-your-im-client](http://lifehacker.com/5469583/how-to-add-facebook-chat-to-your-im-client)

---

### Post by bobpaul on 2010-02-28
The horse's mouth presents the information a little more succinctly. We don't really need a history of Facebook chat to configure our clients.

[http://www.facebook.com/sitetour/chat.php](http://www.facebook.com/sitetour/chat.php)

---

### Post by Theta2evo on 2010-08-05
> **suoko said:**
> terminal solution:

wget [https://bugs.freedesktop.org/attachment.cgi?id=20810](https://bugs.freedesktop.org/attachment.cgi?id=20810)
sudo mv attachment.cgi?id=20810 /usr/share/telepathy/managers/haze.manager
wget [https://bugs.freedesktop.org/attachment.cgi?id=20811](https://bugs.freedesktop.org/attachment.cgi?id=20811)
sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile


i have tired this and it works till i try the last sudo 
i get the message
> [FONT=Arial]mv: cannot move `attachment.cgi?id=20811' to `/usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile': No such file or directory[/FONT]

---

### Post by bobpaul on 2010-08-05
> **Theta2evo said:**
> i have tired this and it works till i try the last sudo 
i get the message
> mv: cannot move `attachment.cgi?id=20811' to `/usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile': No such file or directory

Theta, facebook now uses the XMPP (aka Jabber) protocol, so you can use any jabber client directly. You're getting "No such file" error because bigbrownchunx-facebookim plugin is defucnt and no longer exists.

Follow the instructions [here on Facebook.com](http://www.facebook.com/sitetour/chat.php) to setup facebook chat in Pidgin, Empathy, Adium, or any other XMPP client.

---

### Post by J14e on 2012-06-29
thanks for this thread guys its all working great now

---

### Post by oldos2er on 2012-06-29
Please don't bump old threads.

---

