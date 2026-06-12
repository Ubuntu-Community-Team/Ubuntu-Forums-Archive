---
title: "Update Pidgin to 2.5.3"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by mamous on 2008-12-27
Hi.. 
I would like to tell how to update pidgin 2.5.2 to 2.5.3
[COLOR="Red"][SIZE="3"]1-[/SIZE][/COLOR] u have to download these three files
1- pidgin ([http://www.getdeb.net/download/3611/0]("http://www.getdeb.net/download/3611/0")) (561.6 kB)
2- pidgin-data ([http://www.getdeb.net/download/3611/1]("http://www.getdeb.net/download/3611/1")) (6.9 MB)
3- Libpurple0 ([http://www.getdeb.net/download/3611/2]("http://www.getdeb.net/download/3611/2")) (1.5 MB)
[COLOR="Red"][SIZE="3"]2-[/SIZE][/COLOR] Go to the Synaptic package manager and search for pidgin.
Mark "Pidgin" and "pidgin-data" for removal, it will advise its removing a libpurple0 file as well.
[COLOR="Red"][SIZE="3"]3-[/SIZE][/COLOR] Install the pidgin-data file first (right click and open with the GDebi package installer)
Once pidgin-data is installed then right click on the new libpurple0 installer and install that, then do the same for pidgin.
[COLOR="Red"][SIZE="3"]4-[/SIZE][/COLOR] Start pidgin and it should be working fine.

I hope u enjoy.....

---

### Post by mamous on 2008-12-27
And here is the Version Changes of Pidgin
[COLOR="Red"][SIZE="4"]**libpurple:**[/SIZE][/COLOR]
     * The Buddy State Notification plugin no longer prints duplicate
       notifications when the same buddy is in multiple groups. (Florian
       Quèze)
     * The Buddy State Notification plugin no longer turns JID's, MSN
       Passport ID's, etc. into links. (Florian Quèze)
     * purple-remote now has a "getstatusmessage" command to retrieve
       the text of the current status message.
     * Various fixes to the nullprpl. (Paul Aurich)
     * Fix a crash when accessing the roomlist for an account that's not
       connected. (Paul Aurich)
     * Fix a crash in purple_accounts_delete that happens when this
       function is called before the buddy list is initialized.
       (Florian Quèze)
     * Fix use of av_len in perl bindings to fix some off-by-one bugs
       (Paul Aurich)
     * On ICQ, advertise the ICQ 6 typing capability.  This should fix
       the reports of typing notifications not working with third-party
       clients. (Jaromír Karmazín)
     * Many QQ fixes and improvements, including the ability to connect
       using QQ2008 protocol and sending/receiving of long messages.
       The recommended version to use is still QQ2005.
     * Fix a crash with DNS SRV lookups. (Florian Quèze)
     * Fix a crash caused by authorization requests. (Florian Quèze)

[COLOR="Red"][SIZE="4"]**Gadu-Gadu:**[/SIZE][/COLOR]
     * Add support for IM images. (Adam Strzelecki)
     * Gadu-Gadu now checks that UID's are valid. (Adam Strzelecki)
     * Gadu-Gadu now does proper charset translations where needed. (Adam
       Strzelecki)

[COLOR="Red"][SIZE="4"]**MSN:**[/SIZE][/COLOR]
     * Fix an error with offline messages by shipping the *new*
       "Microsoft Secure Server Authority" and the "Microsoft Internet
       Authority" certificates. These are now always installed even when
       using --with-system-ssl-certs because most systems don't ship
       those intermediate certificates.
     * The Games and Office media can now be set and displayed (in
       addition to the previous Music media). The Media status text now
       shows the album, if possible.
     * Messages sent from a mobile device while you were offline are now
       correctly received.
     * Server transfers after you've been connected for a long time
       should now be handled correctly.
     * Many improvements to handling of "federated" buddies, such as those
       on the Yahoo network.
     * Several known crashes have been resolved.
     * Many other fixes and code cleanup.

[COLOR="Red"][SIZE="4"]**MySpace:**[/SIZE][/COLOR]
     * Respect your privacy settings set using the official MySpace client.
     * Add support for blocking buddies.
     * Fix a bug where buddies didn't appear in their correct groups the
       first time you sign into your account.
     * Properly disconnect and sign out of the service when logging off.
     * Support for foreground and background font colors in outgoing IMs.
     * Support for background font colors in incoming IMs.
     * Many other fixes and code cleanup.

[COLOR="Red"][SIZE="4"]**Sametime:**[/SIZE][/COLOR]
     * Fix insanely long idle times for Sametime 7.5 buddies by assuming
       0 idle time if the idle timestamp is in the future. (Laurent
       Montaron)
     * Fix a crash that can occur on login. (Raiko Nitzsche)

[COLOR="Red"][SIZE="4"]**SIMPLE:**[/SIZE][/COLOR]
     * Fix a crash when a malformed message is received.
     * Don't allow connecting accounts if no server name has been
       specified. (Florian Quèze)

[COLOR="Red"][SIZE="4"]**XMPP:**[/SIZE][/COLOR]
     * Fix the namespace URL we look for in PEP reply stanzas to match
       the URL used in the 'get' requests (Paul Aurich)
     * Resources can be set to the local machine's hostname by using
       __HOSTNAME__ as the resource string. (Jonathan Sailor)
     * Resources can now be left blank, causing the server to generate a
       resource for us where supported. (Jonathan Sailor)
     * Resources now default to no value, but "Home" is used if the
       server refuses to provide a resource.
     * Quit trying to get user info for MUC's. (Paul Aurich)
     * Send "client-accepts-full-bind-result" attribute during SASL
       login. This will fix Google Talk login failures if the user
       configures the wrong domain for his/her account.
     * Support new  element to indicate no XEP-0084 User
       Avatar. (Paul Aurich)
     * Fix SHA1 avatar checksum errors that occur when one of the bytes
       in a checksum begins with 0. (Paul Aurich)
     * Fix a problem with duplicate buddies. (Paul Aurich)

[COLOR="Red"][SIZE="4"]**Yahoo:**[/SIZE][/COLOR]
     * Corrected maximum message lengths for Yahoo!
     * Fix file transfers with older Yahoo protocol versions.

[COLOR="Red"][SIZE="4"]**Zephyr:**[/SIZE][/COLOR]
     * Enable auto-reply, to emulate 'zaway.' (Toby Schaffer)
     * Fix a crash when an account is configured to use tzc but tzc is
       not installed or the configured tzc command is invalid. (Michael
       Terry)
     * Fix a 10 second delay waiting on tzc if it is not installed or the
       configured command is invalid. (Michael Terry)

[COLOR="Red"][SIZE="4"]**Pidgin:**[/SIZE][/COLOR]
     * On GTK+ 2.14 and higher, we're using the gtk-tooltip-delay setting
       instead of our own (hidden) tooltip_delay pref.  If you had
       previously changed that pref, add a line like this to
       ~/.purple/gtkrc-2.0 (where 500 is the timeout (in ms) you want):
           gtk-tooltip-timeout = 500
       To completely disable tooltips (e.g. if you had an old
       tooltip_delay of zero), add this to ~/.purple/gtkrc-2.0:
           gtk-enable-tooltips = 0
     * Moved the release notification dialog to a mini-dialog in the
       buddylist. (Casey Ho)
     * Fix a crash when closing an authorization minidialog with the X
       then immediately going offline. (Paul Aurich)
     * Fix a crash cleaning up custom smileys when Pidgin is closed.
     * Fix adding a custom smiley using the context menu in a conversation
       if no custom smilies have previously been added using the smiley
       manager.
     * Improved support for some message formatting in conversations.
     * Allow focusing the coversation history or userlist with F6.
     * Fixed the Send Button plugin to avoid duplicate buttons in a single
       conversation.
     * Double-clicking a saved status will now activate it and close the
       saved status manager, rather than edit the status.

[COLOR="Red"][SIZE="4"]**Finch:**[/SIZE][/COLOR]
     * Allow binding meta+arrow keys for actions.
     * Added default meta+erase binding for delete previous word.
     * Added "Show When Offline" to buddy menus, so a plugin is no longer
       needed.

---

