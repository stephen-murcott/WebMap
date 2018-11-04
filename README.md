<p align="center">
<img width="300" src="https://i.imgur.com/puyIfHT.jpg" /><br>
A Web Dashbord for Nmap XML Report 
</p>

![WebMap](https://i.imgur.com/BOZVc8e.png)

![WebMap](https://i.imgur.com/33kpQ0J.png)

## Table Of Contents
- [Usage](#usage)
- [Video](#video)
- [Features](#features)
- [XML Filenames](#xml-filenames)
- [CVE and Exploits](#cve-and-exploits)
- [Third Parts](#third-parts)
- [Security Issues](#security-issues)
- [Contributors](#contributors)
- [Contacts](#contacts)

## Usage
You should use this with docker, just by sending this command:
```bash
$ mkdir /tmp/webmap
$ docker run -d \
         --name webmap \
         -h webmap \
         -p 8000:8000 \
         -v /tmp/webmap:/opt/xml \
         rev3rse/webmap

$ # now you can run Nmap and save the XML Report on /tmp/webmap
$ nmap -sT -A -T4 -oX /tmp/webmap/myscan.xml 192.168.1.0/24
```
Now point your browser to http://localhost:8000

### Quick and Dirty
```bash
$ curl -sL http://bit.ly/webmapsetup | bash
```

### Upgrade from previous release
```bash
$ # stop running webmap container
$ docker stop webmap

$ # remove webmap container
$ docker rm webmap

$ # pull new image from dockerhub
$ docker pull rev3rse/webmap

$ # run WebMap
$ curl -sL http://bit.ly/webmapsetup | bash
```

## Video
-- coming soon...

## Features
- Import and parse Nmap XML files
- Statistics and Charts on discovered services, ports, OS, etc...
- Inspect a single host by clicking on its IP address
- Attach labels on a host
- Insert notes for a specific host
- Create a PDF Report with charts, details, labels and notes
- Copy to clipboard as Nikto, Curl or Telnet commands
- Search for CVE and Exploits based on CPE collected by Nmap

## XML Filenames
When creating the PDF version of the Nmap XML Report, the XML filename is used as document title on the first page. 
WebMap will replace some parts of the filename as following:

- `_` will replaced by a space (` `)
- `.xml` will be removed

Example: `ACME_Ltd..xml`<br>
PDF title: `ACME Ltd.`

## CVE and Exploits
thanks to the amazing API services by circl.lu, WebMap is able to looking for CVE and Exploits for each CPE collected by Nmap. 
Not all CPE are checked over the circl.lu API, but only when a specific version is specified 
(for example: `cpe:/a:microsoft:iis:7.5` and not `cpe:/o:microsoft:windows`).

## Network View
![WebMap](https://i.imgur.com/j77jQz9.png)

## Third Parts
- [Django](https://www.djangoproject.com)
- [Materialize CSS](https://materializecss.com)
- [Clipboard.js](https://clipboardjs.com)
- [Chart.js](https://www.chartjs.org)
- [Wkhtmltopdf](https://wkhtmltopdf.org)
- [API cve.circl.lu](https://cve.circl.lu)

## Security Issues
This app is not intended to be exposed on the internet. Please, **DO NOT expose** this app to the internet, use your localhost or, 
in case you can't do it, take care to filter who and what can access to WebMap with a firewall rule or something like that. 
Exposing this app to the whole internet could lead not only to a stored XSS but also to a leakage of sensitive/critical/private 
informations about your port scan. Please, be smart.

## Contributors
This project is currently a beta, and I'm not super skilled on Django so, every type of contribution is appreciated. 
I'll mention all contributors in this section of the README file.

### Contributors List
- s3th_0x [@adubaldo](https://github.com/adubaldo) (bug on single host report)
- Neetx [@Neetx](https://github.com/Neetx) (bug on xml with no host up)

## Contacts
Twitter: [@Menin_TheMiddle](https://twitter.com/Menin_TheMiddle)<br>
YouTube: [Rev3rseSecurity](https://www.youtube.com/rev3rsesecurity)
