---
title: "SPI driver (ADS7843) help required"
date: 2010-10-06
forum: Hardware
---

### Post by varunj on 2010-10-06
Hi, this is my first post here - so excuse me if I go against some norms. Just let me know. 

We are building an embedded system using an RMI Alchemy Au1250 processor, clocked at 500 MHz. This is connected to a touchscreen via the SPI port, with an ADS7843 controller. I think this setup is quite standard. 

Now, since the SPI Master and ADS7846 Touchscreen drivers are both standard drivers they should work straight if provided with the correct initializing data (platform data). This data is provided in platform.c file. The platform data and initialization code that we are using is provided below. This seems to be standard data as we've referenced it from other Linux code. However, we are just doubtful over function db1200_spi_cs_en(). Its functionality, though to do with chipselect is not clear. Could someone please shed some light on this?

I believe the problem is with this platform data, and therefore touch driver is not working as required. There are no fail conditions reached as well and both SPI and ADS7846 drivers get initialized properly without fail.

**The details of the system are:**
Processor: RMI Alchemy Au1250 processor 500 MHz
RAM: 256 MB RAM
Touchscreen: 800x480 resolution 8" 4-wire resistive screen
Linux kernel: 2.6.28 (Official RMI release)
Compiler: mipsel-linux-gcc-sdk-3.4.4

I have attached the schematics, so that you can check the hardware design if required. 

-------------------------------------------------------------
static struct resource psc0_res[] = {
[0] = {
.start = CPHYSADDR(PSC0_BASE_ADDR),
.end = CPHYSADDR(PSC0_BASE_ADDR) + 0x000fffff,
.flags = IORESOURCE_MEM,
},
[1] = {
.start = AU1200_PSC0_INT,
.end = AU1200_PSC0_INT,
.flags = IORESOURCE_IRQ,
},
[2] = {
.start = DSCR_CMD0_PSC0_TX,
.end = DSCR_CMD0_PSC0_TX,
.flags = IORESOURCE_DMA,
},
[3] = {
.start = DSCR_CMD0_PSC0_RX,
.end = DSCR_CMD0_PSC0_RX,
.flags = IORESOURCE_DMA,
},
};

//SPI Touchscreen
static int ads7843_pendown_state(void)
{
unsigned long tcr=0;
unsigned long tmp;

tcr = au_readl(GPIO2_PINSTATE);

tmp = (tcr & 0x0080)>>7;
if(tmp==1)	 // checking for the PX bit is sufficient.
return(0);	 // pen up
else
return(1);	 // pen down
}

static struct ads7846_platform_data db1200_ads7846_data = 
{
.model	 = 7843,
.x_min	 = 150,
.x_max	 = 3830,
.y_min	 = 190,
.y_max	 = 3830,
.vref_delay_usecs	= 100,
.x_plate_ohms	 = 450,
.y_plate_ohms	 = 250,
.pressure_max	 = 15000,
.debounce_max	 = 1,
.debounce_rep	 = 0,
.debounce_tol	 = (~0),
.get_pendown_state	= ads7843_pendown_state,
};

static struct spi_board_info db1200_spi_devs[] __initdata = 
{
{
.modalias	= "ads7846",
.chip_select	= 1, //3,
.max_speed_hz	= 125000 * 16, //125000 * 26,	/* (max sample rate @ 3V) * (cmd + data + overhead) */
.bus_num	= 0,
.platform_data	= &db1200_ads7846_data,
.irq	 = AU1200_GPIO_207,
},
};

static void db1200_spi_cs_en(struct au1550_spi_info *spi, int cs, int pol)
{
if (cs)
{
printk(KERN_INFO " platform.c: db1200_spi_cs_en 1\n"); //dks
bcsr->resets |= BCSR_RESETS_SPISEL;
}
else
{
printk(KERN_INFO " platform.c: db1200_spi_cs_en 0\n"); //dks
bcsr->resets &= ~BCSR_RESETS_SPISEL;
}
}

static struct au1550_spi_info db1200_spi_platdata = {
.mainclk_hz = 50000000, /* PSC0 clock */
.num_chipselect = 2,
.activate_cs = db1200_spi_cs_en,
};

static u64 spi_dmamask = DMA_32BIT_MASK;

static struct platform_device spi_dev = {
.dev = {
.dma_mask = &spi_dmamask,
.coherent_dma_mask = DMA_32BIT_MASK,
.platform_data = &db1200_spi_platdata,
},
.name = "au1550-spi",
.id = 0, /* bus number */
.num_resources = ARRAY_SIZE(psc0_res),
.resource = psc0_res,
};

static struct platform_device *board_platform_devices[] __initdata = {
&ide_device,
&smc91c111_device, //dks(,)
&spi_dev //dks
};

static int __init board_register_devices(void)
{

printk(KERN_INFO " Platform.c: board_register_devices\n");	
spi_register_board_info(db1200_spi_devs, ARRAY_SIZE(db1200_spi_devs)); //dks
return platform_add_devices(board_platform_devices,
ARRAY_SIZE(board_platform_devices));
}

-------------------------------------------------------------

If you need any additional information please let me know.

Thank you,

Regards,
Varun

---

### Post by varunj on 2010-10-06
Just to mention the problems we are facing: After the first 3-4 touch events, no more touch events are recorded after that and the sensitivity of the clicks is very weak. Also, when the screen is touched while a video is playing the video and audio pause for the duration of the touch. 

One of the problems could be that the aforementioned SPI connection is multiplexed (74CBELV3257) with an on-board battery and RTC (DS1339), but we are disabling that, so don't think this should effect it.

---

### Post by varunj on 2010-10-09
Sorry for the bump, but this problem has really put us in a bottleneck. 

Any suggestions at all? If any of you feel I'd be better posting on another, more relevant forum, please point me in that direction. 

Thanks!

---

