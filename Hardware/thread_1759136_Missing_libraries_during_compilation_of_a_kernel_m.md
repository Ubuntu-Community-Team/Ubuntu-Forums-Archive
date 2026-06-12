---
title: "Missing libraries during compilation of a kernel module"
date: 2011-05-15
forum: Hardware
---

### Post by paolino_hc on 2011-05-15
Hi guys, i'm newbie in this forum.
I have some trouble comppiling a simple kernel module. I have to implement a driver for  a pci express card.
So i'm tryng with something a bit simple in order to understand how it works. I seem that the problem is some lybraries missing. I'm working with 2.6.32-31-generic kernel and i have installed the kernel-headers. 
This is my code to compile:
> 
//Definizione delle librerie
#include <linux/init.h>
#include <linux/config.h>
#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/slab.h>
#include <linux/fs.h>
#include <linux/errno.h>
#include <linux/types.h>
#include <linux/proc_fs.h>
#include <linux/fcntl.h>

#include <asm/system.h>
#include <asm/uaccess.h>

MODULE_LICENSE ("Dual BSD/GPL");

//Dichiarazione delle funzioni di memory.c (prototipi)
int memory_open(struct inode *inode, struct file *filp);
int memory_release(struct inode *inode, struct file *filp);
ssize_t memory_read(struct file *filp, char *buf, size_t count, loff_t *f_pos);
ssize_t memory_write(struct file *filp, char *buf, size_t count, loff_t *f_pos);

//Variabili globali del driver (major number e buffer dove salvare i dati)
int memory_major = 60;
char *memory_buf;

//Accesso alle funzioni
struct file_operations memory_fops = {
    read : memory_read,
    write : memory_write,
    open : memory_open,
    release : memory_release };

//Inizializzazione modulo memory
int memory_init(void) {
    int result ;
    
    //Registrazione dispositivo
    result = register_chrdev(memory_major, "memory", &memory_fops);
    if(result<0) {
        printk(KERN_ALERT "MEMORY: impossibile ottenere il major number \n");
        return result;
    }
    
    //Allocazione memoria per il buffer
    memory_buf = kmalloc(1,GFP_KERNEL);
    if(!memory_buf) {
        result = -ENOMEM;
        goto fail;
    }
    memset(memory_buf, 0, 1);
    
    printk(KERN_ALERT "Inserito modulo memoria \n");
    return 0;
    
    fail:
      memory_exit(),
      return result;
}

//Uscita modulo memory
void memory_exit(void) {
    unregister_chrdev(memory_major, "memory");
    if(memory_buf) kfree(memory_buf);
    printk(KERN_ALERT "Rimozione modulo memory \n");
}

//Apertura device
int memory_open(struct inode *inode, struct file *filp) {
    printk(KERN_ALERT "Apertura del dispositivo \n");
    return 0;
}

//Chiusura device
int memory_release(struct inode *inode, struct file *filp) {
    printk(KERN_ALERT "Chiusura del dispositivo \n");
    return 0; 
}

//Lettura device
ssize_t memory_read(struct file *filp, char *buf, size_t count, loff_t *f_pos) {
    
    //Trasferimento dati nello 'user space'
    copy_to_user(buf,memory_buf,1);
    printk(KERN_ALERT "Lettura dati eseguita \n");
    
    //Cambiamento posizione di lettura
    if(*f_pos == 0) {
        *f_pos += 1;
        return 1;
    }
    else return 0;
}

//Scrittura device
ssize_t memory_write(struct file *filp, char *buf, size_t count, loff_t *f_pos) {
    char *tmp;
    
    tmp=buf+count-1;
    copy_from_user(memory_buf,tmp,1);
    printk(KERN_ALERT "Scrittura dati eseguita \n");
    return 1;
}

//Dichiarazione funzioni init e exit
module_init(memory_init);
module_exit(memory_exit);the compilation result tell me that something is missing:

[PHP]paolo@paolo-laptop:~/Scrivania$ gcc memory.c -o memory
memory.c:2:24: error: linux/init.h: No such file or directory
memory.c:3:26: error: linux/config.h: No such file or directory
memory.c:4:26: error: linux/module.h: No such file or directory
memory.c:6:24: error: linux/slab.h: No such file or directory
memory.c:10:27: error: linux/proc_fs.h: No such file or directory
In file included from /usr/include/asm/fcntl.h:1,
                 from /usr/include/linux/fcntl.h:4,
                 from memory.c:11:
/usr/include/asm-generic/fcntl.h:96: error: expected specifier-qualifier-list before ‘pid_t’
memory.c:13:24: error: asm/system.h: No such file or directory
memory.c:14:25: error: asm/uaccess.h: No such file or directory
memory.c:16: error: expected declaration specifiers or ‘...’ before string constant
memory.c:16: warning: data definition has no type or storage class
memory.c:19: warning: ‘struct file’ declared inside parameter list
memory.c:19: warning: its scope is only this definition or declaration, which is probably not what you want
memory.c:19: warning: ‘struct inode’ declared inside parameter list
memory.c:20: warning: ‘struct file’ declared inside parameter list
memory.c:20: warning: ‘struct inode’ declared inside parameter list
memory.c:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_read’
memory.c:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_write’
memory.c:29: error: variable ‘memory_fops’ has initializer but incomplete type
memory.c:30: error: unknown field ‘read’ specified in initializer
memory.c:30: error: ‘memory_read’ undeclared here (not in a function)
memory.c:30: warning: excess elements in struct initializer
memory.c:30: warning: (near initialization for ‘memory_fops’)
memory.c:31: error: unknown field ‘write’ specified in initializer
memory.c:31: error: ‘memory_write’ undeclared here (not in a function)
memory.c:31: warning: excess elements in struct initializer
memory.c:31: warning: (near initialization for ‘memory_fops’)
memory.c:32: error: unknown field ‘open’ specified in initializer
memory.c:32: warning: excess elements in struct initializer
memory.c:32: warning: (near initialization for ‘memory_fops’)
memory.c:33: error: unknown field ‘release’ specified in initializer
memory.c:33: warning: excess elements in struct initializer
memory.c:33: warning: (near initialization for ‘memory_fops’)
memory.c: In function ‘memory_init’:
memory.c:42: error: ‘KERN_ALERT’ undeclared (first use in this function)
memory.c:42: error: (Each undeclared identifier is reported only once
memory.c:42: error: for each function it appears in.)
memory.c:42: error: expected ‘)’ before string constant
memory.c:47: error: ‘GFP_KERNEL’ undeclared (first use in this function)
memory.c:52: warning: incompatible implicit declaration of built-in function ‘memset’
memory.c:54: error: expected ‘)’ before string constant
memory.c:59: error: expected expression before ‘return’
memory.c: At top level:
memory.c:63: warning: conflicting types for ‘memory_exit’
memory.c:58: note: previous implicit declaration of ‘memory_exit’ was here
memory.c: In function ‘memory_exit’:
memory.c:66: error: ‘KERN_ALERT’ undeclared (first use in this function)
memory.c:66: error: expected ‘)’ before string constant
memory.c: At top level:
memory.c:70: warning: ‘struct file’ declared inside parameter list
memory.c:70: warning: ‘struct inode’ declared inside parameter list
memory.c:70: error: conflicting types for ‘memory_open’
memory.c:19: note: previous declaration of ‘memory_open’ was here
memory.c: In function ‘memory_open’:
memory.c:71: error: ‘KERN_ALERT’ undeclared (first use in this function)
memory.c:71: error: expected ‘)’ before string constant
memory.c: At top level:
memory.c:76: warning: ‘struct file’ declared inside parameter list
memory.c:76: warning: ‘struct inode’ declared inside parameter list
memory.c:76: error: conflicting types for ‘memory_release’
memory.c:20: note: previous declaration of ‘memory_release’ was here
memory.c: In function ‘memory_release’:
memory.c:77: error: ‘KERN_ALERT’ undeclared (first use in this function)
memory.c:77: error: expected ‘)’ before string constant
memory.c: At top level:
memory.c:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_read’
memory.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_write’
memory.c:107: warning: data definition has no type or storage class
memory.c:107: warning: parameter names (without types) in function declaration
memory.c:108: warning: data definition has no type or storage class
memory.c:108: warning: parameter names (without types) in function declaration[/PHP]I don't know which is the problem. Can anyone help me please?
I saw that some missing libraries that should be under the directory /usr/include are under the directory /usr/src/linus-headers-2.6.32-31-generic/usr/include. 

Thanks you very much...any usefull information will be very appreciated

---

