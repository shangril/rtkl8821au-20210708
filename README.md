##### [Click for USB WiFi Adapter Information for Linux](https://github.com/morrownr/USB-WiFi)

-----

### 8821au ( 8821au.ko ) :rocket:

### Linux Driver for USB WiFi Adapters that are based on the RTL8811AU and RTL8821AU Chipsets

- v5.12.5.2 (Realtek) (20210708)
- Plus updates from the Linux community

### Features

- IEEE 802.11 b/g/n/ac WiFi compliant
- 802.1x, WEP, WPA TKIP and WPA2 AES/Mixed mode for PSK and TLS (Radius)
- IEEE 802.11b/g/n/ac Client mode
  * Support wireless security for WEP, WPA TKIP and WPA2 AES PSK
  * Support site survey scan and manual connect
  * Support power saving mode
- Supported interface modes
  * IBSS
  * Managed
  * AP
  * P2P-client
  * P2P-GO
- Log level control
- Power saving control
- VHT control (allows 80 MHz channel width in AP mode)
- SU Beamformee and MU Beamformee control
- SU Beamformer control

### Compatible CPUs

- x86, amd64
- ARM, ARM64

### Compatible Kernels

- Kernels: 4.15 - 5.11 (Realtek)
- Kernels: 5.12 - 5.15 (community support)

### Tested Linux Distributions

- Arch Linux (kernel 5.4)
- Arch Linux (kernel 5.9)

- Debian 11 (kernel 5.10)

- Fedora (kernel 5.11)

- Linux Mint 20.2 (Linux Mint based on Ubuntu) (kernel 5.11)

- LMDE 4 (Linux Mint based on Debian) (kernel 4.19)

- Manjaro 20.1 (kernel 5.9)

- Raspberry Pi OS (2021-01-11) (ARM 32 bit) (kernel 5.10)
- Raspberry Pi Desktop (x86 32 bit) (kernel 4.19)

- Ubuntu 21.04 (kernel 5.11)
- Ubuntu 20.10 (kernel 5.8)
- Ubuntu 20.04 (kernel 5.4)

### Download Locations for Tested Linux Distributions

- [Arch Linux](https://www.archlinux.org)
- [Debian](https://www.debian.org/)
- [Fedora](https://getfedora.org)
- [Linux Mint](https://www.linuxmint.com)
- [Manjaro](https://manjaro.org)
- [Raspberry Pi OS](https://www.raspberrypi.org)
- [Ubuntu](https://www.ubuntu.com)

### Tested Hardware

- [Alfa AWUS036ACS 802.11ac AC600 Wi-Fi Wireless Network Adapter](https://www.amazon.com/gp/product/B0752CTSGD)

### Compatible Devices

* Alfa AWUS036ACS
* Buffalo WI-U2-433DHP
* Edimax EW-7811UTC
* Edimax EW-7811UAC
* Edimax EW-7811UCB
* ELECOM WDC-433DU2H
* GMYLE - AC450
* Netgear A6100
* Planex GW-450S
* TP Link T2U Nano
* TP Link T2U Plus
* Numerous adapters that are based on the supported chipsets.

Note: Please read "supported-device-IDs" for information about how to confirm the correct driver for your adapter.

### Installation Information

The installation instructions are for the novice user. Experienced users are welcome to alter the installation to meet their needs.

Temporary internet access is required for installation. There are numerous ways to enable temporary internet access depending on your hardware and situation. [One method is to use tethering from a phone.](https://www.makeuseof.com/tag/how-to-tether-your-smartphone-in-linux) Another method to enable temporary internet access is to keep a [wifi adapter that uses an in-kernel driver](https://github.com/morrownr/USB-WiFi) in your toolkit.

You will need to use the terminal interface. The quick way to open a terminal: Ctrl+Alt+T (hold down on the Ctrl and Alt keys then press the T key)

DKMS is used for the installation. DKMS is a system utility which will automatically recompile and install this driver when a new kernel is installed. DKMS is provided by and maintained by Dell.

It is recommended that you do not delete the driver directory after installation as the directory contains information and scripts that you may need in the future.

There is no need to disable Secure Mode to install this driver. If Secure Mode is properly setup on your system, this installation will support it.

### Installation Steps

Step 1: Open a terminal (Ctrl+Alt+T)

Step 2: Update the system (select the option for the OS you are using)
```
    Option for Debian based distributions such as Ubuntu, Linux Mint, Kali and Raspberry Pi OS

    $ sudo apt update
```
```
    Option for Arch based distributions such as Manjaro

    $ sudo pacman -Syu
```
```
    Option for Fedora based distributions

    # sudo dnf -y update
```
Step 3: Install the required packages (select the option for the OS you are using)
```
    Option for Raspberry Pi OS

    $ sudo apt install -y raspberrypi-kernel-headers bc build-essential dkms git
```
```
    Option for Debian, Kali or Linux Mint Debian Edition (LMDE)

    $ sudo apt install -y linux-headers-$(uname -r) build-essential dkms git libelf-dev
```
```
    Option for Ubuntu (all flavors) or Linux Mint

    $ sudo apt install -y dkms git build-essential
```
```
    Options for Arch or Manjaro

    if using pacman

    $ sudo pacman -S --noconfirm linux-headers dkms git

    Note: If you are asked to choose a provider, make sure to choose the one that
    corresponds to your version of the linux kernel (for example, "linux510-headers"
    for Linux kernel version 5.10) if you install the incorrect version, you'll have
    to uninstall it and reinstall the correct version.

    if using other methods, please follow the instructions provided by those methods

```

```
    Option for Fedora

    # sudo dnf -y install git dkms kernel-devel kernel-debug-devel
```
Step 4: Create a directory to hold the downloaded driver

```bash
$ mkdir ~/src
```
Step 5: Move to the newly created directory
```bash
$ cd ~/src
```
Step 6: Download the driver
```bash
$ git clone https://github.com/morrownr/8821au-20210708.git
```
Step 7: Move to the newly created driver directory
```bash
$ cd ~/src/8821au-20210708
```
Step 8: Warning: this step only applies if you are installing to Raspberry Pi *hardware*.

Run a preparation script
```
    Option for 32 bit operating systems to be installed to Raspberry Pi hardware

    $ ./raspi32.sh
```
```
    Option for 64 bit operating systems to be installed to Raspberry Pi hardware

    $ ./raspi64.sh

    Note: I will only address issues having to do with the 64 bit version of the
    Raspberry Pi OS once it is out of beta and is released as generally available.
```
Step 9: Run the installation script (For automated builds, use _NoPrompt_ as an option)
```bash
$ sudo ./install-driver.sh [NoPrompt]
```
Step 10: Reboot
```bash
$ sudo reboot
```

### Driver Options

A file called `8821au.conf` will be installed in `/etc/modeprobe.d` by default.

Location: `/etc/modprobe.d/8821au.conf`

This file will be read and applied to the driver on each system boot.

To edit the driver options file, run the `edit-options.sh` script.
```bash
$ sudo ./edit-options.sh
```
Documentation for Driver Options is included in the file `8821au.conf`.

### Removal of the Driver

Note: This script should be used in the following situations:

- the driver is no longer needed
- a fresh start with default settings is needed
- a new version of the driver needs to be installed
- a major operating system upgrade is going to be applied

Note: This script removes everything that has been installed, with the exception
of the packages installed in Step 3 and the driver directory. The driver directory
can and probably should be deleted in most cases after running the script.

Step 1: Open a terminal (Ctrl+Alt+T)

Step 2: Move to the driver directory
```bash
$ cd ~/src/8821au-20210708
```
Step 3: Run the removal script
```bash
$ sudo ./remove-driver.sh
```
Step 4: Reboot
```bash
$ sudo reboot
```
### Recommended WiFi Router/ Access Point Settings

Note: These are general recommendations, some of which may not apply to your specific situation.

Security: Set WPA2-AES. Do not set WPA2 mixed mode or WPA or TKIP.

Channel width for 2.4G: Set 20 MHz fixed width. Do not use 40 MHz or 20/40 automatic.

Channels for 2.4G: Set channel 1 or 6 or 11 depending on the congestion at your location. Do not set automatic channel selection.

Mode for 2.4G: For best performance, set "N only" if you no longer use B or G capable devices.

Network names: Do not set the 2.4G Network and the 5G Network to the same name. Note: Unfortunately many routers come with both networks set to the same name.

Channels for 5G: Not all devices are capable of using DFS channels. It may be necessary to set a fixed channel in the range of 36 to 48 or 149 to 161 in order for all of your devices to work on 5g. (for US, other countries may vary)

Best location for the wifi router/ access point: Near center of apartment or house, at least a couple of feet away from walls, in an elevated location.

Check congestion: There are apps available for smart phones that allow you to check the congestion levels on wifi channels. The apps generally go by the name of WiFi Analyzer or something similar.

After making and saving changes, reboot the router.


### Set regulatory domain to correct setting in OS

Check the current setting
```bash
$ sudo iw reg get
```

If you get 00, that is the default and may not provide optimal performance.

Find the correct setting here: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2

Set it temporarily
```bash
$ sudo iw reg set US
```
Note: Substitute your country code if you are not in the United States.

Set it permanently
```bash
$ sudo nano /etc/default/crda

Change the last line to read:

REGDOMAIN=US
```

### Recommendations regarding USB

- Moving your USB WiFi adapter to a different USB port has been known to fix a variety of problems. Problems include WiFi going on and off as well as connections coming and going.

- If connecting your USB WiFi adapter to a desktop computer, use the USB ports on the rear of the computer. Why? The ports on the rear are directly connected to the motherboard which will reduce problems with interference and disconnection that can happen with front ports that use cables.

- If your USB WiFi adapter is USB 3 capable then plug it into a USB 3 port.

- Avoid USB 3.1 Gen 2 ports if possible as almost all currently available adapters have been tested with USB 3.1 Gen 1 (aka USB 3) and not with USB 3.1 Gen 2.

- If you use an extension cable and your adapter is USB 3 capable, the cable needs to be USB 3 capable.

- Some USB WiFi adapters require considerable electrical current and push the capabilities of the power available via USB port. One example is devices that use the Realtek 8814au chipset. Using a powered multiport USB extension can be a good idea in cases like this.


### How to disable onboard WiFi on Raspberry Pi 3B, 3B+, 3A+, 4B and Zero W.

Add the following line to /boot/config.txt
```
dtoverlay=disable-wifi
```

### How to forget a saved WiFi network on a Raspberry Pi

1. Edit wpa_supplicant.conf
```bash
$ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
2. Delete the relevant WiFi network block (including the 'network=' and opening/closing braces.

3. Press ctrl-x followed by 'y' and enter to save the file.

4. Reboot