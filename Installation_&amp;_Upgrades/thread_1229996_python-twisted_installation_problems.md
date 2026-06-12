---
title: "python-twisted installation problems"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Owsley on 2009-08-02
i attempted to use synaptic to install the ubuntustudio-audio package and it came up with the following error message:

E: python-twisted-conch: subprocess post-installation script returned error exit status 1
E: python-twisted-mail: subprocess post-installation script returned error exit status 1
E: python-twisted-web: subprocess post-installation script returned error exit status 1
E: python-twisted-lore: dependency problems - leaving unconfigured
E: python-twisted-names: subprocess post-installation script returned error exit status 1
E: python-twisted-news: subprocess post-installation script returned error exit status 1
E: python-twisted-runner: subprocess post-installation script returned error exit status 1
E: python-twisted-words: subprocess post-installation script returned error exit status 1
E: python-twisted: dependency problems - leaving unconfigured
E: ardour: dependency problems - leaving unconfigured
E: ubuntustudio-audio: dependency problems - leaving unconfigured

any thoughts as to what these errors mean?

---

### Post by Partyboi2 on 2009-08-02
Hi, can you open a terminal and post the output to
```
sudo dpkg --configure -a
``` if its a long output wrap them in the "[code]" tags.

---

### Post by Owsley on 2009-08-03
```
Setting up python-twisted-conch (1:8.2.0-2) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/avatar.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/checkers.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/agent.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/connect.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/default.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/direct.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/options.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/client/unix.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/error.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/colors.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/helper.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/insults.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/text.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/insults/window.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/interfaces.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ls.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/manhole.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/manhole_ssh.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/manhole_tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/mixin.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/openssh_compat/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/openssh_compat/factory.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/openssh_compat/primes.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/recvline.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/scripts/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/scripts/cftp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/scripts/ckeygen.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/scripts/conch.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/scripts/tkconch.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/agent.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/asn1.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/channel.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/common.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/connection.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/factory.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/filetransfer.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/forwarding.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/keys.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/service.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/session.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/sexpy.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/transport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ssh/userauth.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/stdio.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/telnet.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/keydata.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_cftp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_channel.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_conch.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_connection.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_filetransfer.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_helper.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_insults.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_keys.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_manhole.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_mixin.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_recvline.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_ssh.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_telnet.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_text.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_transport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_userauth.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/test/test_window.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ttymodes.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ui/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ui/ansi.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/ui/tkvt100.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/conch/unix.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/plugins/twisted_conch.py not found.
Setting up python-twisted-web (8.2.0-2) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/plugins/twisted_web.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/demo.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/distrib.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/domhelpers.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/error.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/google.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/guard.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/html.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/http.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/microdom.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/monitor.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/proxy.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/resource.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/rewrite.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/script.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/server.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/soap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/static.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/sux.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_cgi.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_distrib.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_domhelpers.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_http.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_mvc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_proxy.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_soap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_static.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_web.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_webclient.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_woven.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_xml.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/test/test_xmlrpc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/trp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/twcgi.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/util.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/vhost.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/widgets.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/FlashConduit.fla not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/FlashConduit.swf not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/FlashConduitGlue.html not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/WebConduit2_mozilla.js not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/WebConduit2_msie.js not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/WebConduitGlue.html not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/controller.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/dirlist.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/flashconduit.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/form.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/guard.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/input.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/interfaces.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/model.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/page.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/simpleguard.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/tapestry.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/template.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/utils.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/view.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/woven/widgets.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/web/xmlrpc.py not found.
Setting up python-twisted-runner (8.2.0-0ubuntu1) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/inetd.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/inetdconf.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/inetdtap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/portmap.c not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/procmon.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/runner/procutils.py not found.
Setting up python-twisted-words (8.2.0-2) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/plugins/twisted_words.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/ewords.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/baseaccount.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/basechat.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/basesupport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/gtkaccount.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/gtkchat.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/gtkcommon.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/instancemessenger.glade not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/interfaces.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/ircsupport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/jyaccount.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/jychat.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/locals.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/pbsupport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/proxyui.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/im/tocsupport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/iwords.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/irc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/component.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/error.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/ijabber.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/jid.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/jstrports.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/sasl.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/sasl_mechanisms.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/xmlstream.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/jabber/xmpp_stringprep.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/msn.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/oscar.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/protocols/toc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/scripts/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/scripts/im.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/service.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_basesupport.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_domish.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_irc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabberclient.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabbercomponent.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabbererror.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabberjid.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabbersasl.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabbersaslmechanisms.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabberxmlstream.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_jabberxmppstringprep.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_msn.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_service.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_toc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_xishutil.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_xmlstream.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/test/test_xpath.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/toctap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/domish.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/utility.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/xmlstream.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/xpath.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/xpathparser.g not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/words/xish/xpathparser.py not found.
Setting up python-twisted-mail (8.2.0-2) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/alias.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/bounce.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/imap4.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/mail.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/maildir.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/pb.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/pop3.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/pop3client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/protocols.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/relay.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/relaymanager.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/scripts/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/scripts/mailmail.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/smtp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/pop3testserver.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/rfc822.message not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_bounce.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_imap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_mail.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_options.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_pop3.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_pop3client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/mail/test/test_smtp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/plugins/twisted_mail.py not found.
Setting up python-twisted-news (8.2.0-2) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/database.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/news.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/nntp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/test/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/test/test_news.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/news/test/test_nntp.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/plugins/twisted_news.py not found.
Setting up python-twisted-names (8.2.0-0ubuntu1) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/_version.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/authority.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/cache.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/common.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/dns.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/error.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/hosts.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/resolve.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/root.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/secondary.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/server.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/srvconnect.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/tap.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/test_cache.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/test_client.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/test_dns.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/test_names.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/test_rootresolve.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/names/test/test_srvconnect.py not found.
   dpkg: /usr/lib/python2.5/site-packages/twisted/plugins/twisted_names.py not found.

```

---

### Post by Owsley on 2009-08-21
bump

---

