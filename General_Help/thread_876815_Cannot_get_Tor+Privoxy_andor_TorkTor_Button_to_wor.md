---
title: "Cannot get Tor+Privoxy and/or Tork/Tor Button to work within Ubuntu"
date: 2008-08-01
forum: General Help
---

### Post by theravenproject on 2008-08-01
I have been trying to configure Tor for a week now...I have been on google more than I have slept, and these forums and The Tor website as well...no luck!  When I first reinstalled Hardy and went and got Tork-it after going through the installation and setup according to the insttructions it said there was an error (In Tork) and that it could not connect to Tor/Privoxy-I tried uninstalling purging all and reinstalling several different times with no luck...as I am really uneducated about regular anonymous proxies and my life/freedom depends on anonymity at times I really need Tor to work until I can become adept at using traditional proxification techniques.  Can someone walk me through a step by step install of Tor and Privoxy + a method of using it such as Tor button for Firefox...I also need to be able to use it via the command prompt with apps like ettercap/dsniff or regular Bash functions/commands.
  Basically I need to install both and configure it so that when I choose to-any way that my computer could possibly connect to the web is anonymized with Tor.  Please help me-Anyone who has done this ver same thing on their own Hardy box please can you walk me through your install the same way?  **Accepting any and all HELP_Desperate!**
                 Thanks Before Hand "cos I know someone willl Help

---

### Post by mordak13 on 2008-08-01
If you are using it for/with Firefox, install tor which you did already and then get the Firefox addon called Foxyproxy [https://addons.mozilla.org/en-US/firefox/addon/2464]("https://addons.mozilla.org/en-US/firefox/addon/2464") it could not be simpler. You don't need Privoxy with Foxyproxy. It will walk you through setup when you restsrt Firefox. I don't use Tor in any other way, just with Firefox so I can't help you further.

---

### Post by theravenproject on 2008-08-01
Okay but without Privoxy will Tor work in my tewrminal while doing things like Zone Transfers/ any other Terminal Online Apps/Activity?

---

### Post by mordak13 on 2008-08-01
> **theravenproject said:**
> Okay but without Privoxy will Tor work in my tewrminal while doing things like Zone Transfers/ any other Terminal Online Apps/Activity?

I'm not sure. I know you can tunnel through Tor and run Tor hidden services but I don't know how as I've never needed to. You'd have to read up on Tor and Privoxy's man pages or howto's specifically to find out more or wait for someone who knows more about it than I do. Sorry man. :(

---

### Post by El Rogueo on 2008-08-17
> **theravenproject said:**
> Okay but without Privoxy will Tor work in my tewrminal while doing things like Zone Transfers/ any other Terminal Online Apps/Activity?

I'm having similar problems passing a config to Tor through Tork, but I can tell you that FoxyProxy is specifically a proxy made for Firefox.

In response to your question, no, foxyproxy will NOT function the same way Privoxy protects you in terminal programs.

---

