---
title: "firefox: how to disable security warning in shell settings"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by derek-w on 2009-07-26
Hello,

I use firefox along with XVfb server to generate thumbshots.

when I access some sites there appears an alert box, saying:

"The information you have entered is to be sent over an unencrypted connection and could.. "

How can I turn off the warning?

My pref.js file looks like that:

user_pref("alerts.totalOpenTime", 1);
user_pref("app.update.enabled", false);
user_pref("app.update.lastUpdateTime.addon-background-update-timer", 1180678656);
user_pref("app.update.lastUpdateTime.background-update-timer", 1180609657);
user_pref("browser.sessionstore.enabled", false);
user_pref("browser.sessionstore.resume_from_crash", false);
user_pref("browser.startup.page", 0);
user_pref("extensions.lastAppVersion", "1.5.0.12eol");
user_pref("network.cookie.prefsMigrated", true);
user_pref("plugin.default_plugin_disabled", false);
user_pref("privacy.popups.disable_from_plugins", 3);
user_pref("security.enable_ssl2", false);
user_pref("security.enable_ssl3", false);





thanks.

---

### Post by wojox on 2009-07-26
Click Edit > Prefrences > Security > Warning Messages

---

### Post by derek-w on 2009-07-26
but I do not have GUI.

how do I access "Edit > Prefrences > Security > Warning Messages" from command line?

---

### Post by derek-w on 2009-07-27
is it possible at all?

---

### Post by derek-w on 2009-07-28
does anyone know?

---

