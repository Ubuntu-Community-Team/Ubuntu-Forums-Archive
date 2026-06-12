---
title: "HELP! - ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)"
date: 2008-09-03
forum: General Help
---

### Post by VolvoPunch on 2008-09-03
Whats wrong? How can I fix this? I need some guidance. 
```

root@test-corp-esx-03:/opt/SUNWut/sbin# ./utconfig

Configuration of Sun Ray Core Services Software

This script automates the configuration of the Sun Ray Core Services
software and related software products.  Before proceeding, you should
have read the Sun Ray Core Services 4.0 Installation Guide and filled out
the Configuration Worksheet.  This script will prompt you for the values
you filled out on the Worksheet.  For your convenience, default values
(where applicable) are shown in brackets.

Continue ([y]/n)? y
Enter Sun Ray admin password:
Re-enter Sun Ray admin password:

Configure Sun Ray Web Administration? ([y]/n)? y
Enter Apache Tomcat installation directory [/opt/apache-tomcat]:

An Apache Tomcat webserver does not exist at the given location
(/opt/apache-tomcat/conf/server.xml is missing).
You can either reenter the path or skip the configuration of the
Sun Ray Web Administration component to continue with the configuration
of the remaining SRSS components.
If you skip the configuration of this component then the admin GUI will not work                                                                              .
You can retry the configuration of this component later by calling
'utconfig -w'. As a prerequisite you need to install a Tomcat webserver.
It is available in the SRSS Image 'Supplemental/Apache_Tomcat' directory.

Reenter or skip? ([r]/s): r
Enter Apache Tomcat installation directory [/opt/apache-tomcat]: /usr/local/tomcat                                                                              at
Enter HTTP port number [1660]:
Enable secure connections? ([y]/n)? n
Enter Tomcat process username [utwww]:
Enable remote server administration? (y/[n])? y

Configure Sun Ray Kiosk Mode? (y/[n])? y

Enter user prefix [utku]:

Enter group [utkiosk]:

Enter userID range start [150000]:

Enter number of users [25]:


Configure this server for a failover group? (y/[n])? n

About to configure the following software products:

Sun Ray Data Store 3.0
    Hostname: test-corp-esx-03
    Sun Ray root entry: o=utdata
    Sun Ray root name: utdata
    Sun Ray utdata admin password: (not shown) 
    SRDS 'rootdn': cn=admin,o=utdata

Sun Ray Web Administration
    Apache Tomcat installation directory: /usr/local/tomcat
    HTTP port number: 1660
    HTTPS port: Disabled
    Tomcat process username: utwww
    Remote server administration: Enabled

Sun Ray Core Services 4.0
    Failover group: no
    Sun Ray Kiosk Mode: yes

Sun Ray Kiosk Mode 4.0
  User name prefix:   utku
  Base user ID:       150000
  Number of accounts: 25
  Kiosk group name:   utkiosk
  Kiosk group ID:     auto

Continue ([y]/n)? y

Updating Sun Ray Data Store schema ...

Updating Sun Ray Data Store ACL's ...

Creating Sun Ray Data Store ...

Restarting Sun Ray Data Store ...
Starting Sun Ray Data Store daemon .
Tue Sep  2 13:51 : utdsd starting

Loading Sun Ray Data Store ...

Executing '/usr/bin/ldapadd -h test-corp-esx-03 -x -p 7012 -D cn=admin,o=utdata'                                                                               ...
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

Added 18 new LDAP entries.

Creating Sun Ray Core Services Configuration ...
Adding user account for 'utwww' (ut admin web server user) ...done
Sun Ray Web Administration enabled to start at system boot.

Unique "/etc/opt/SUNWut/gmSignature" has been generated.

Restarting Sun Ray Data Store ...
Stopping Sun Ray Data Store daemon
Sun Ray Data Store daemon stopped
Starting Sun Ray Data Store daemon .
Tue Sep  2 13:51 : utdsd starting
Adding user admin ...
Failed to add user(s) to the list

Creating new Sun Ray Kiosk Mode configuration ...

Validating new user ids.
Validating new user accounts.
Creating kiosk group utkiosk
Configuring new kiosk user accounts:
.........................
25 users configured
ERROR: Could not retrieve policy.
ERROR: Could not retrieve policy.

***********************************************************
The current policy has been modified.  You must restart the
authentication manager to activate the changes.
***********************************************************


Configuration of Sun Ray Core Services has completed.  Please check
the log file, /var/log/SUNWut/utconfig.2008_09_02_13:50:10.log, for errors.
root@test-corp-esx-03:/opt/SUNWut/sbin# cd ..

```

---

### Post by MsTBSoX on 2008-09-03
[font=Arial][[size=3][color=red]In 2008 Beijing Olympic Games[/color][/size]](http://wangluozhuanqian.org)[color=silver][size=1] Britain sports delegation has made the [/size][size=1]cmmings[/size][/color][/font][font=Arial][size=1][color=silver] historical progress, wins 19 golden 13 silver 15 copper altogether [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.net)[font=Arial][size=1][color=silver]medals, [/color][/size][/font][[font=Arial][size=1][color=silver]**cmmings**[/color][/size][/font]](http://cmmings.cn/)[font=Arial][size=1][color=silver] arranges in gold medal announcement 4th, and breaks two [/color][/size][/font][[font=Arial][size=1][color=silver]**world**[/color][/size][/font]](http://wangluozhuanqian.org/)[font=Arial][size=1][color=silver] records. Had the historical leap as [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.org)[font=Arial][size=1][color=silver] Olympic Games host country Britain sports.[/color][/size][/font]

---

### Post by BaBeBiLaaaa on 2008-09-08
**[Buy Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[Sell Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by VolvoPunch on 2008-09-11
Bump for a solution!

---

### Post by 080729jk on 2008-10-30
&#25105;&#20204;&#26159;&#19987;&#19994;&#33268;&#21147;&#20110;&#32593;&#32476;&#26381;&#21153;&#30340;&#19968;&#20010;&#22242;&#38431;.&#25105;&#20204;&#20026;&#24744;&#25552;&#20379;&#19987;&#19994;&#30340;&#32593;&#31449;&#24314;&#35774;&#26381;&#21153;&#65281;[**&#19996;&#33694;google&#20248;&#21270;**](http://www.71668.net/dwgoogleyh.htm)&#25105;&#20204;&#25317;&#26377;&#19987;&#19994;&#30340;&#32593;&#31449;&#24314;&#35774;&#24037;&#31243;&#24072;,&#26377;&#19987;&#38376;&#30340;&#37096;&#38376;&#36127;&#36131;&#32593;&#31449;&#30340;&#32500;&#25252;.[**&#28145;&#22323;google&#20248;&#21270;**](http://www.71668.net/szgoogleyh.htm)&#26377;&#19987;&#19994;&#30340;&#21672;&#35810;&#24072;&#20026;&#24744;&#35299;&#31572;&#24314;&#31449;&#20197;&#21450;&#32593;&#31449;&#32500;&#25252;&#26041;&#38754;&#30340;&#38382;&#39064;**.**[**&#32593;&#39029;&#35774;&#35745;&#20844;&#21496;**](http://www.71668.net/wysjgs.htm)&#24744;&#21482;&#38656;&#35201;&#24456;&#23569;&#30340;&#25237;&#36164;&#23601;&#33021;&#35753;&#24744;&#30340;&#20225;&#19994;&#26377;&#19968;&#20010;&#33258;&#24049;&#30340;&#32593;&#32476;&#24179;&#21488;,[**&#23425;&#27874;google&#20248;&#21270;**](http://www.71668.net/nbgoogleyh.htm)&#24744;&#21482;&#35201;&#35828;&#20986;&#24744;&#30340;&#35201;&#27714;&#25105;&#20204;&#20250;&#20026;&#24744;&#26009;&#29702;&#19968;&#20999;. &#35802;&#23454;&#23432;&#20449;&#26159;&#25105;&#20204;&#30340;&#35834;&#35328;[**google&#20248;&#21270;&#26041;&#26696;**](http://www.71668.net/googleyhfa.htm)&#35753;&#23458;&#25143;&#28385;&#24847;&#26159;&#25105;&#20204;&#30340;&#23447;&#26088; &#32473;&#22823;&#23478;&#25552;&#20379;101%&#30340;&#28385;&#24847;&#24230;&#26159;&#25105;&#20204;&#30340;&#30446;&#26631;&#12290;

---

### Post by Sef on 2008-10-30
> Please check
the log file, /var/log/SUNWut/utconfig.2008_09_02_13:50:10.log, for errors.


What error message(s) are you getting?

---

### Post by aaron_nimocks on 2008-12-26
> **VolvoPunch said:**
> Bump for a solution!

Looking for the same thing over here. Any help at all for this?

---

