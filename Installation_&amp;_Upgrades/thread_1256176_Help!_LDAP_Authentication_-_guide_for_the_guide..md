---
title: "Help! LDAP Authentication - guide for the guide."
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by Augsburg on 2009-09-02
Hi.

I recently installed an LDAP server on a 9.04 server. Now I am trying to setup a client to authenticate against it. I followed instructions at [https://help.ubuntu.com/community/LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication"), but near the bottom it gets a little choppy, and I'm not sure what's optional and what isn't. Below is the how-to I created during my install:

> 
ldap-howto

############
## SERVER ##
############

sudo apt-get install slapd
	set password.
sudo apt-get install ldap-utils
sudo mv /etc/ldap/slapd.d /etc/ldap/slapd.d.old
sudo mv /var/backups/unk*ldapdb /var/backups/unknown-2.4.11-0ubuntu3.ldapdb.old (if this doesn't remove anything, fine)
sudo dpkg-reconfigure slapd
	Omit OpenLDAP server configuration? [no]
	DNS domain name: [augsburg.com]
	Organization name: [Augsburg]
	Database backend to use: [HDB]
	Do you want the database to be removed when slapd is purged? [no]
*	Move old database? [yes]
	Allow LDAPv2 protocol? [no]

Create the file sa1.ldif:
	dn: ou=staff,dc=augsburg,dc=com
	changetype: add
	objectClass: organizationalUnit
	ou: staff

ldapmodify -xD "cn=admin,dc=augsburg,dc=com" -W -f sa1.ldif

if this fails, restart slapd (sudo /etc/init.d/slapd restart), then retry the above command.

sudo adduser phil
	(set password to "phil")

Create the file sa2.ldif (here, with user phil):
	dn: cn=phil,ou=staff,dc=augsburg,dc=com
	changetype: add
	cn: phil
	objectClass: inetOrgPerson
	sn: phil

ldapmodify -xD "cn=admin,dc=augsburg,dc=com" -W -f sa2.ldif

Check everything:
	sudo slapcat

############
## CLIENT ##
############

sudo apt-get install libpam-ldap libnss-ldap nss-updatedb libnss-db
During setup:
	LDAP server Uniform Resource Identifier: 
		ldap://<server ip address>
	Distinguished name of the search base:
		dc=augsburg,dc=com
	LDAP version to use:
		[3]
	Make local root Database admin:
		[yes]
	Does the LDAP database require login?
		[no]
	LDAP account for root:
        	cn=admin,dc=augsburg,dc=com
        LDAP root account password:
        	[ldap admin password]
        	
sudo nano /etc/nsswitch.conf
	change:
		passwd:         compat
		group:          compat
	to:
		passwd:         files ldap
		group:          files ldap

sudo nano /etc/pam.d/common-account
	comment out all lines and add these lines:
		#changed for LDAP Setup
		account sufficient      pam_ldap.so
		account required        pam_unix.so

sudo nano /etc/pam.d/common-auth
	comment out all lines and add these lines:
		#changed for LDAP setup
		auth    required        pam_group.so    use_first_pass
		auth    sufficient      pam_ldap.so
		auth    required        pam_unix.so     nullok_secure   use_first_pass

sudo nano /etc/pam.d/common-password
	comment out all lines and add these lines:
		#changed for LDAP setup
		password	sufficient	pam_ldap.so
		password	required	pam_unix.so nullok obscure min=4 max=8 md5

REBOOT (wait for client to shutdown)


---

