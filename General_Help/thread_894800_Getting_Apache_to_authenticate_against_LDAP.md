---
title: "Getting Apache to authenticate against LDAP"
date: 2008-08-19
forum: General Help
---

### Post by dynacrylic on 2008-08-19
I'm trying to get apache to authenticate using ldap. I'm running 8.04.

I've installed the following mods added them to httpd.conf:
```
LoadModule ldap_module /usr/lib/apache2/modules/mod_ldap.so
LoadModule authnz_ldap_module /usr/lib/apache2/modules/mod_authnz_ldap.so
```

Here is what my entry looks like in 000-default:

```
# testing LDAP
<Directory /var/www/ldap/>
	Order deny,allow
	Deny from All
	AuthName "My Intranet"
	AuthType Basic
	AuthLDAPBindDN  bindusername
	AuthLDAPBindPassword bindpassword
	AuthBasicProvider ldap
	AuthzLDAPAuthoritative off
	AuthLDAPUrl "ldap://mail.myuniversity.edu/ou=campus,dc=mail,dc=myuniversity,dc=edu?cn"
	Require valid-user
	Satisfy any
</Directory>
# end testing LDAP
```

I am able to create a session and search ldap server with JXplore using the information above, but I just can't seem to get authentication to work. (Actually JXplore requires university\bindusername to work)

I've also checked error.log, but I didn't see anything that would help resolve/troubleshoot my problem.

Any recommendations/suggestions?

---

### Post by Titan8990 on 2008-08-19
I have never done that directly with apache but everytime I have authed something to LDAP I had to specify a base dn to begin searching. It would look something like this:

cn=admin,ou=users,dn=TEST,dn=local

---

### Post by dynacrylic on 2008-08-20
> **Titan8990 said:**
> I have never done that directly with apache but everytime I have authed something to LDAP I had to specify a base dn to begin searching. It would look something like this:

cn=admin,ou=users,dn=TEST,dn=local

I've tried the following before I create this post and none of it seemed to help

```
LDAP_Server mail.myuniversity.edu
LDAP_Port 389
Base_DN "dc=mail,dc=myuniversity,dc=edu"
UID_Attr cn
```

I do have a line like yours similar when I connect using JXlpore though.

---

### Post by dynacrylic on 2008-08-20
I changed the 000-default to include this instead:

```
# testing LDAP
<Directory /var/www/ldap/>
                AuthBasicProvider ldap
                AuthType Basic
                AuthName "My Intranet"
                AuthLDAPUrl ldap://mail.myuniversity.edu:389/ou=campus,dc=mail,dc=myuniversity,dc=edu?cn
                AuthLDAPBindDN cn=mybindusername,dc=mail,dc=myuniversity,dc=edu
                AuthLDAPBindPassword "bindpassword"
                Require valid-user
</Directory>
# end testing LDAP
```

That did not work. 

Below is what in the error log trying 3 different ways logging in:

```
[Wed Aug 20 14:03:39 2008] [debug] mod_authnz_ldap.c(377): [client 172.1.0.101] [10329] auth_ldap authenticate: using URL ldap://mail.myuniversity.edu:389/ou=campus,dc=mail,dc=myuniversity,dc=edu?cn
[Wed Aug 20 14:03:39 2008] [warn] [client 172.1.0.101] [10329] auth_ldap authenticate: user testusername authentication failed; URI /ldap [LDAP: ldap_simple_bind_s() failed][Invalid credentials]
[Wed Aug 20 14:03:39 2008] [error] [client 172.1.0.101] user testusername: authentication failure for "/ldap": Password Mismatch
[Wed Aug 20 14:03:57 2008] [debug] mod_authnz_ldap.c(377): [client 172.1.0.101] [10330] auth_ldap authenticate: using URL ldap://mail.myuniversity.edu:389/ou=campus,dc=mail,dc=myuniversity,dc=edu?cn
[Wed Aug 20 14:03:57 2008] [warn] [client 172.1.0.101] [10330] auth_ldap authenticate: user myuniversity\\testusername authentication failed; URI /ldap [LDAP: ldap_simple_bind_s() failed][Invalid credentials]
[Wed Aug 20 14:03:57 2008] [error] [client 172.1.0.101] user myuniversity\\testusername: authentication failure for "/ldap": Password Mismatch
[Wed Aug 20 14:04:28 2008] [debug] mod_authnz_ldap.c(377): [client 172.1.0.101] [10331] auth_ldap authenticate: using URL ldap://mail.myuniversity.edu:389/ou=campus,dc=mail,dc=myuniversity,dc=edu?cn
[Wed Aug 20 14:04:28 2008] [warn] [client 172.1.0.101] [10331] auth_ldap authenticate: user myuniversity/testusername authentication failed; URI /ldap [LDAP: ldap_simple_bind_s() failed][Invalid credentials]
[Wed Aug 20 14:04:28 2008] [error] [client 172.1.0.101] user myuniversity/testusername: authentication failure for "/ldap": Password Mismatch
```

---

### Post by Titan8990 on 2008-08-20
Try authenticating to the LDAP server remotely. Use a packet sniffer such as wireshark to see exactly what response the LDAP server is sending back. This was very helpful to me when i was authenticating a XAMP server to LDAP.

---

### Post by dynacrylic on 2008-08-22
I finally got it working! (I get a little passionate about things like this.) Below are some crude instructions how I got my interal server to authenticate apache with my university's LDAP (which is Active Directory I believe). 

First, make sure you have mod_ldap installed **and make sure mod_ldap is enabled**. (*Yes, as simple as it sounds I didn't have it enabled*). 

To see if you have mod_ldap, check in /etc/apache2/mods-available/:
```
ldap.load -> ../mods-available/ldap.load
```
If you don't have it, download the apache2.2-common package in Synaptic Package Manager or use apt-get in the shell.

If you have mod_ldap already, check /etc/apache2/mods-enabled/ to see if it is enabled. If mod_ldap is enabled, it will look like this:
```
ldap.load -> ../mods-available/ldap.load
```
If mod_ldap is not enabled, use the following command to enable it:
```

sudo a2enmod ldap
```
Verify that it is enabled.

*I did not change my /etc/apache2/httpd.conf file (except adding mod_rewrite which was for another application)*
```
LoadModule ldap_module /usr/lib/apache2/modules/mod_ldap.so
LoadModule authnz_ldap_module /usr/lib/apache2/modules/mod_authnz_ldap.so
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
```
*I'm unclear as to why I had to enable the mod_ldap using the a2enmod command because I had enabled it here.*

For the /etc/apache2/sites-enabled/000-default I have the following config for my test LDAP directory:
```

# testing LDAP
  <Directory /var/www/ldap/>
    Order deny,allow
    Deny from All
    AuthName "Intranet"
    AuthType Basic
    AuthBasicProvider ldap
    AuthzLDAPAuthoritative off
    AuthLDAPUrl ldap://mail.myUniversity.edu/ou=campus,dc=myUniversity,dc=edu?cn
    AuthLDAPBindDN "myBindUsername@myUniversity"
    AuthLDAPBindPassword "myBindPassword"
    Require valid-user
    Satisfy any
  </Directory>
# end testing LDAP
```

Most example configs I saw have the "mail" part as "ldap", but I used mail.myUniversity.edu. (I stumbled across this working set-up literally by "brute-force" just exhausting variations of templates and configs I saw elsewhere)

I may have changed other settings along the way, of which I apologize for not keeping track of. 

This might not be the proper, most efficient and safest way to get apache to authenticate against LDAP, but it works. *At least I'll have this post as another backup for our internal server's configuration.*

---

### Post by dynacrylic on 2008-08-23
Additional information others might find handy:

For specific users in LDAP:
```
Require ldap-user userName1 userName2
```

For a specific user group in LDAP, I used the following:
```
Require ldap-group CN=myGroup,OU=myGroup,OU=User Managed Groups,DC=myUniversity,DC=edu
```
**The user group information was obtained by connecting to the LDAP server using JXplore LDAP Browser and doing a search for the group (using cn). For me, the group was listed under the User Managed Groups; it also included all the names of people who are in the group. The distinguishedName attribute type held the necessary information.*

---

### Post by hardstatic on 2009-04-23
Set Apache loglevel to debug and check for the following output from the Apache error.log:

[FONT="Lucida Console"][LDAP: ldap_simple_bind_s() failed][Invalid credentials][/FONT]

If you're getting that error, focus on adjusting your bind credentials.

This is my working config for basic authentication against an Active Directory server with Apache2.2 :

```
<Location />
   AuthType Basic
   AuthBasicProvider ldap
   AuthzLDAPAuthoritative off
   AuthName "Apache LDAP"

   Order allow,deny
   Allow from All
   Require valid-user

   AuthLDAPBindDN "cn=binduser,ou=group,dc=server,dc=domain"
   AuthLDAPBindPassword password
   AuthLDAPURL "ldap://my.activedirectory.server:389/ou=group,dc=server,dc=domain?sAMAccountName?sub?(objectClass=*)"
</Location>
```

---

