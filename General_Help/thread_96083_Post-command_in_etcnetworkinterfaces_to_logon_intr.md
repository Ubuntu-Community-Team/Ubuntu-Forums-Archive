---
title: "Post-command in /etc/network/interfaces to logon intranet"
date: 2005-11-28
forum: General Help
---

### Post by daller on 2005-11-28
Hi There,

Here at my school the wireless network is not encrypted, instead we are forwarded to "https://hp760wl.ibc.dk:443/logon" the first time we try to access the internet!

Is there a way I can make "ifup eth1" do all the work for me?

This is the page:

```


<!DOCTYPE html
        PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
        "DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en-US"><head><title>Hewlett-Packard Company Secure Logon</title></head>
<body bgcolor="#ffffff" onload="document.forms.logonForm.username.focus(); document.forms.logonForm.javaworks.value = 1" scroll="auto">

<form method="post" action="https://hp760wl.ibc.dk:443/logon" enctype="application/x-www-form-urlencoded" name="logonForm">

<INPUT name=query_string type=hidden value=""><INPUT name=javaworks type=hidden value=0>
<INPUT name=vernier_id type=hidden value="hp">
<INPUT name=product_id type=hidden value="VNSS">
<INPUT name=releast_id type=hidden value="1.0">
<INPUT name=logon_status type=hidden value="1">
<INPUT name=guest_allowed type=hidden value="0">
<INPUT name=realm_required type=hidden value="0">
<INPUT name=secret type=hidden value="6440b7892f96fe167b0e11f16a709e99a8ee6368499d8f184269938ba32757c3433a58944b56a608bcb468a9d07ad71c">
<INPUT name=verify_vernier type=hidden value="1db74e2f1d0c3be993a2402550ad74bc">

<table cellspacing="0" cellpadding="1" border="0" width="500" bgcolor="#666699"><tr><td><table cellspacing="0" cellpadding="5" border="0" width="100%"><tr><td align="center" bgcolor="#666699"><font size="4" color="#ffffff"><b>Registered Users</b></font></td></tr><tr><td align="center" bgcolor="#ffffff"><table cellspacing="0" cellpadding="2" border="0"><tr align="right"><td><font size="2">Username:</font></td><td><font size="2"><input type="text" name="username" size="15"></font></td></tr><tr align="right"><td><font size="2">Password:</font></td><td><font size="2"><input type="password" name="password" size="15"></font></td></tr></table></td></tr><tr><td align="center" bgcolor="#ffffff"><input name="logon_action" type="submit" value="Logon User"></td></tr></table></td></tr></table><p></font>

</form>


```

The "secret" (see the code) will probably be hard to hack?

---

