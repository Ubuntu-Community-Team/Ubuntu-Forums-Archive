---
title: "Problem with iSCSI connected LTO-2 drive"
date: 2016-12-10
forum: Hardware
---

### Post by David_Partridge on 2016-12-10
I did:

```
root@Charon:/home/amonra# mt -f /dev/st0 fsf 1
mt: /dev/st0: rmtioctl failed: Input/output error
root@Charon:/home/amonra#
```

The rmtioctl message appeared after about 10-15 seconds, and the iSCSI target showed that the session had dropped after another 10-15 seconds.

When I was returned to the command line prompt, the target showed the session as connected again.

During most/all of this time the forward space file operation was still running.

```
root@Charon:/home/amonra# iscsiadm -m node --targetname "iqn.2008-08.com.starwindsoftware:mercury-ultrium2" --portal "192.168.129.77:3260" 
# BEGIN RECORD 2.0-873
node.name = iqn.2008-08.com.starwindsoftware:mercury-ultrium2
node.tpgt = -1
node.startup = manual
node.leading_login = No
iface.hwaddress = <empty>
iface.ipaddress = <empty>
iface.iscsi_ifacename = default
iface.net_ifacename = <empty>
iface.transport_name = tcp
iface.initiatorname = <empty>
iface.bootproto = <empty>
iface.subnet_mask = <empty>
iface.gateway = <empty>
iface.ipv6_autocfg = <empty>
iface.linklocal_autocfg = <empty>
iface.router_autocfg = <empty>
iface.ipv6_linklocal = <empty>
iface.ipv6_router = <empty>
iface.state = <empty>
iface.vlan_id = 0
iface.vlan_priority = 0
iface.vlan_state = <empty>
iface.iface_num = 0
iface.mtu = 0
iface.port = 0node.discovery_address = 192.168.129.77
node.discovery_port = 3260
node.discovery_type = send_targets
node.session.initial_cmdsn = 0
node.session.initial_login_retry_max = 8
node.session.xmit_thread_priority = -20
node.session.cmds_max = 128
node.session.queue_depth = 32
node.session.nr_sessions = 1
node.session.auth.authmethod = None
node.session.auth.username = <empty>
node.session.auth.password = <empty>
node.session.auth.username_in = <empty>
node.session.auth.password_in = <empty>
node.session.timeo.replacement_timeout = 120
node.session.err_timeo.abort_timeout = 15
node.session.err_timeo.lu_reset_timeout = 30
node.session.err_timeo.tgt_reset_timeout = 30
node.session.err_timeo.host_reset_timeout = 60
node.session.iscsi.FastAbort = Yes
node.session.iscsi.InitialR2T = No
node.session.iscsi.ImmediateData = Yes
node.session.iscsi.FirstBurstLength = 262144
node.session.iscsi.MaxBurstLength = 16776192
node.session.iscsi.DefaultTime2Retain = 0
node.session.iscsi.DefaultTime2Wait = 2
node.session.iscsi.MaxConnections = 1
node.session.iscsi.MaxOutstandingR2T = 1
node.session.iscsi.ERL = 0
node.conn[0].address = 192.168.129.77
node.conn[0].port = 3260
node.conn[0].startup = manual
node.conn[0].tcp.window_size = 524288
node.conn[0].tcp.type_of_service = 0
node.conn[0].timeo.logout_timeout = 15
node.conn[0].timeo.login_timeout = 15
node.conn[0].timeo.auth_timeout = 45
node.conn[0].timeo.noop_out_interval = 5
node.conn[0].timeo.noop_out_timeout = 5
node.conn[0].iscsi.MaxXmitDataSegmentLength = 0
node.conn[0].iscsi.MaxRecvDataSegmentLength = 262144
node.conn[0].iscsi.HeaderDigest = None
node.conn[0].iscsi.DataDigest = NoneThe return to the command prompt took a while longer.

node.conn[0].iscsi.IFMarker = No
node.conn[0].iscsi.OFMarker = No
# END RECORD
root@Charon:/home/amonra#
``` 

Can anyone advise what the problem may be?  I'm guessing this has something to do with iSCSI timeout settings.  If so what should I change and to what?

Thanks, Dave

---

### Post by David_Partridge on 2016-12-15
It would appear that the guilty party was:

node.conn[0].timeo.noop_out_interval = 5
node.conn[0].timeo.noop_out_timeout = 5

Basically the iSCSI target couldn't respond to the NOP-out polls while processing the lengthy command to the tape drive, and the iSCSI initiator threw an error when it didn't get a response to its NOP-out.

I changed both of these to 0 for the tape device and the problem went away.

Please  note that the README.gz for open-scsi doesn't actually say that this is  what you need to do to disable the NOP-out polling, so could I suggest  that this be stated explicitly. 

I must admit that I find it hard  to imagine that an iSCSI target would reply to a NOP-out while it was  processing a command such as a tape fsf or even tape erase (whose  timeout is 6 * the long-timeout of 4 hours).  Should perhaps the NOP-out  polling be suspended while a command is being processed?  Or  alternatively maybe the NOP-out polling be completely disabled by  default with something in the README.gz file that explains WHEN you  might want it and how to enable it.   It's certainly clear that (at  least) the MS iSCSI initiator doesn't send NOP-out polls.

Regards
Dave

---

