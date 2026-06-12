---
title: "invalid msg, error number 22 while sending routing header in ipv6 domain"
date: 2008-10-31
forum: General Help
---

### Post by shekharban on 2008-10-31
Invalid argument: error 22 while using sendmsg to routing header (ipv6)


Hi, 

Below is the raw socket program for sending routing header in ipv6 domain. My 
source address is fe80::21d:9ff:fe17:58c7 and destination address is fe80::21d
:9ff:fe17:5d0e in the below example. When i run this i am getting invalid 
argument with sendmsg, with error number 22. Could any one please help me out 
with this. 

#include <sys/types.h>
#include <netinet/in.h>
#include <netinet/ip6.h>
#include <errno.h>
#include <string.h>

void main()
{
int sock_fd;
int on = 1; 
int offset = 4;
int ret = 0;

struct sockaddr_in6 *daddr;
struct in6_pktinfo pinfo;
struct msghdr msg;
struct cmsghdr *cmsg;
struct iovec *iovector;
socklen_t rthlen = 0;
int cmsglen;

sock_fd = socket(AF_INET6, SOCK_RAW, IPPROTO_IPV6);

if(sock_fd < 0)
{
printf("\nClient: Socket Creation Failed: Error %d\n", errno);
return;
}

iovector = (struct iovec*)calloc(1, sizeof(struct iovec));


/* Since for Mobility Header the checksum is located in offset 4, we need to
* set the offset to 4 
*/ 
if (setsockopt(sock_fd, IPPROTO_IPV6, IPV6_RECVRTHDR, &on, sizeof(on)) < 0)
{
printf("\nClient: RTHDR option set failed\n");
return;
}

/* Our Destination Address is fe80::21d:9ff:fe17:5d0e eth0 interface
* i.e. fe80:0:0:0:021d:09ff:fe17:5d0e
*/
daddr = (struct sockaddr_in6*)calloc(1, sizeof(struct sockaddr_in6));

daddr->sin6_family = AF_INET6;

daddr->sin6_addr.s6_addr16[0] = 0xfe80;
daddr->sin6_addr.s6_addr16[1] = 0x0;
daddr->sin6_addr.s6_addr16[2] = 0x0;
daddr->sin6_addr.s6_addr16[3] = 0x0;
daddr->sin6_addr.s6_addr16[4] = 0x021d;
daddr->sin6_addr.s6_addr16[5] = 0x09ff;
daddr->sin6_addr.s6_addr16[6] = 0xfe17;
daddr->sin6_addr.s6_addr16[7] = 0x5d0e;

daddr->sin6_port = htons(IPPROTO_IPV6);

/* Our Source Address is fe80::21d:9ff:fe17:58c7 eth0 interface
* i.e. fe80:0:0:0:021d:09ff:fe17:58c7
*/
memset(&pinfo, 0, sizeof(struct in6_pktinfo));

pinfo.ipi6_addr.s6_addr16[0] = 0xfe80;
pinfo.ipi6_addr.s6_addr16[1] = 0x0;
pinfo.ipi6_addr.s6_addr16[2] = 0x0;
pinfo.ipi6_addr.s6_addr16[3] = 0x0;
pinfo.ipi6_addr.s6_addr16[4] = 0x021d;
pinfo.ipi6_addr.s6_addr16[5] = 0x09ff;
pinfo.ipi6_addr.s6_addr16[6] = 0xfe17;
pinfo.ipi6_addr.s6_addr16[7] = 0x58c7;
pinfo.ipi6_ifindex = 2; /* Interface Id */


/* Fill the Routing Header in ancillary data */
rthlen = inet6_rth_space(IPV6_RTHDR_TYPE_0, 1); //return #bytes required for 
Routing header
cmsglen = CMSG_SPACE(rthlen);
printf("\nClient: rthlen is %d\n", rthlen);
cmsg = malloc(cmsglen);
if (cmsg == NULL)
{
printf("\nClient:Ancillary Data memory allocation failed\n");
return;
}

memset(cmsg, 0, cmsglen);
memset(&msg, 0, sizeof(msg));

iovector->iov_base = malloc(10);
iovector->iov_len = 10;

strcpy(iovector->iov_base, "TEST-4-RH");

msg.msg_control = (void *)cmsg;
msg.msg_controllen = cmsglen;
msg.msg_iov = iovector;
msg.msg_iovlen = 1;
msg.msg_name = (void *)daddr;
msg.msg_namelen = sizeof(struct sockaddr_in6);

void *rthp;

cmsg = CMSG_FIRSTHDR(&msg);

cmsg->cmsg_len = CMSG_LEN(rthlen);
cmsg->cmsg_level = IPPROTO_IPV6;
cmsg->cmsg_type = IPV6_RTHDR;

rthp = CMSG_DATA(cmsg);
rthp = inet6_rth_init(rthp, rthlen, IPV6_RTHDR_TYPE_0, 1);

if(rthp == NULL)
{
printf("\nClient: Routing Header Init failed\n");
return;
}

inet6_rth_add(rthp, &daddr->sin6_addr);

ret = sendmsg(sock_fd, &msg, 0);

rthp = NULL;
if (ret < 0)
{
printf("\nClient:Send Message Failed: Error %d Ret %d\n", errno, ret);
free(iovector->iov_base);
free(iovector);
return;
}
}

Thanks in advance,
shekhar

---

