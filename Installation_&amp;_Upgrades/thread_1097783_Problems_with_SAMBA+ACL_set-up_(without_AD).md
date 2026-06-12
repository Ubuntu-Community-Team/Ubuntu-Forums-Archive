---
title: "Problems with SAMBA+ACL set-up (without AD)"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by klausmedk on 2009-03-16
Hello!

I'm running samba 3.2.3 on my Ubuntu 8.10 server installation.

I'm trying to use ACL in order to get extended user permission administration, but cannot make it work.

My samba shares are on a ext3 partition, and i have enabled ACL in fstab. setting and getting ACL permissions on my files directly works like a charm.

But when my users try to access files via samba they cannot access their files even though ACL permissions on the files are set to give them full access.

first of all how can I check wheter ACL is indeed enabled in my samba installation? 
"smbd -b | grep -i acl" yields:

HAVE_SYS_ACL_H
HAVE_ACL_LIBACL_H
HAVE_POSIX_ACLS
pdb_ldap pdb_smbpasswd pdb_tdbsam rpc_lsarpc rpc_winreg rpc_initshutdown rpc_dssetup rpc_wkssvc rpc_svcctl2 rpc_ntsvcs2 rpc_netlogon rpc_netdfs rp
c_srvsvc rpc_spoolss rpc_eventlog2 rpc_samr idmap_ldap idmap_tdb idmap_passdb idmap_nss nss_info_template auth_sam auth_unix auth_winbind auth_server
auth_domain auth_builtin vfs_default vfs_posixacl

Is that ok?
My server is nowhere near a domain in any way.
I've tried any combinations of the following settings on my shares without success:

nt acl support = yes
inherit acls = yes
acl map full control = yes

Am I missing some additional settings to enable ACL on my shares?
Normal samba access works fine...e.g. by specifying "valid users = xxx,yyy" in my samba config. But I expect that this setting is not required if i wish to simply make samba obey ACL permissions?

Regards
//Klaus

---

