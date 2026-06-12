---
title: "DNS issues."
date: 2008-09-14
forum: General Help
---

### Post by jeff.sadowski on 2008-09-14
I recently started having issues connecting to yahoo chat. It turns out it is an issue with DNS. My home router seems to reply with an incomplete packet, but not always. It only does DNS on UDP and scs.msg.yahoo.com sometimes has a large list of ips sometimes enough that I guess it doesn't fit on a UDP packet and sends an incomplete packet that most unix programs will ignore because it is incomplete.

dig and nslookup on scs.msg.yahoo.com fail as follows
;; Truncated, retrying in TCP mode.
;; Connection to 192.168.0.1#53(192.168.0.1) for scs.msg.yahoo.com
failed: connection refused.

I need to learn more about truncation so that I can get qwest to fix the issue.

Are there some good DNS entries that consistently have something like 20 ips on one name so that I can get it to fail all the time.

---

### Post by bab1 on 2008-09-14
Jeff,

This looks like a DNS roblem, but not of the type you may think it is.
> dig and nslookup on scs.msg.yahoo.com fail as follows
;; Truncated, retrying in TCP mode.
;; [COLOR="Red"]Connection to 192.168.0.1#53([/COLOR]192.168.0.1) for scs.msg.yahoo.com
failed: connection refused.


The part I highlighted in red shows the connection to the host 192.168.0.1 on port #53 and being refused.  Port #53 is the normal TCP/UDP port for DNS.  I assume that this IP address is for your router (mine is set up that way).  I think you have a firewall problem.  Do you have a firewall on the router?  If so allow port 53 to be open for your requests.  DNS should then work.

Edit: Here is what I get from dig.  You will see that It queries my home router (192.168.1.1) first:```
bruce@malibu:~>dig scs.msg.yahoo.com

; <<>> DiG 9.4.1-P1.1 <<>> scs.msg.yahoo.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56349
;; flags: qr rd ra; QUERY: 1, ANSWER: 27, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;scs.msg.yahoo.com.             IN      A

;; ANSWER SECTION:
scs.msg.yahoo.com.      1659    IN      A       66.163.181.173
scs.msg.yahoo.com.      1659    IN      A       66.163.181.174
scs.msg.yahoo.com.      1659    IN      A       66.163.181.175
scs.msg.yahoo.com.      1659    IN      A       66.163.181.176
scs.msg.yahoo.com.      1659    IN      A       66.163.181.177
scs.msg.yahoo.com.      1659    IN      A       66.163.181.178
scs.msg.yahoo.com.      1659    IN      A       66.163.181.179
scs.msg.yahoo.com.      1659    IN      A       66.163.181.180
scs.msg.yahoo.com.      1659    IN      A       66.163.181.181
scs.msg.yahoo.com.      1659    IN      A       66.163.181.182
scs.msg.yahoo.com.      1659    IN      A       66.163.181.183
scs.msg.yahoo.com.      1659    IN      A       66.163.181.184
scs.msg.yahoo.com.      1659    IN      A       66.163.181.185
scs.msg.yahoo.com.      1659    IN      A       66.163.181.186
scs.msg.yahoo.com.      1659    IN      A       66.163.181.187
scs.msg.yahoo.com.      1659    IN      A       66.163.181.188
scs.msg.yahoo.com.      1659    IN      A       66.163.181.189
scs.msg.yahoo.com.      1659    IN      A       66.163.181.193
scs.msg.yahoo.com.      1659    IN      A       66.163.181.106
scs.msg.yahoo.com.      1659    IN      A       66.163.181.107
scs.msg.yahoo.com.      1659    IN      A       66.163.181.166
scs.msg.yahoo.com.      1659    IN      A       66.163.181.167
scs.msg.yahoo.com.      1659    IN      A       66.163.181.168
scs.msg.yahoo.com.      1659    IN      A       66.163.181.169
scs.msg.yahoo.com.      1659    IN      A       66.163.181.170
scs.msg.yahoo.com.      1659    IN      A       66.163.181.171
scs.msg.yahoo.com.      1659    IN      A       66.163.181.172

;; Query time: 7 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Sep 14 18:58:30 2008
;; MSG SIZE  rcvd: 467

```

---

