<h1 align="center">Zeek Intel Framework Diagram</h1>




```mermaid

flowchart TD
    A["Threat Intelligence - IOCs"] -->|IPs, Subnet, Domains, URLs, File Hashes, Software names, File names, email addresses, Cert Hashes, Public Key Hashes | B["Zeek Intel Framework - Compares Threat Intel DB against Zeek log stream"]
    A1["Zeek logs stream"] -->|"Conn::IN_ORIG, Conn::IN_RESP, Files::IN_HASH, Files::IN_NAME, DNS::IN_REQUEST, DNS::IN_RESPONSE, HTTP::IN_HOST_HEADER, HTTP::IN_REFERRER_HEADER, HTTP::IN_USER_AGENT_HEADER, HTTP::IN_X_FORWARDED_FOR_HEADER, HTTP::IN_URL, SMTP::IN_MAIL_FROM, SMTP::IN_RCPT_TO, SMTP::IN_FROM, SMTP::IN_TO, SMTP::IN_CC, SMTP::IN_RECEIVED_HEADER, SMTP::IN_REPLY_TO, SMTP::IN_X_ORIGINATING_IP_HEADER, SMTP::IN_MESSAGE, SSH::IN_SERVER_HOST_KEY, SSL::IN_SERVER_NAME, SMTP::IN_HEADER, X509::IN_CERT, SMB::IN_FILE_NAME, SSH::SUCCESSFUL_LOGIN"| B
   

    B --> C1["Match Seen"]
    B --> C2["No Match"]
  

    C1 --> D["intel.log generated"]
    C2 --> D1["No log generated"]
 ```
-------------------------------------------------------------
<h3 align="center">intel.log examples:</h3>

    
```
{
  "ts": "2019-03-12T18:22:19.252191Z",
  "uid": "Cpue7J1KNReqCodXHc",
  "id.orig_h": "192.168.4.6",
  "id.orig_p": 64738,
  "id.resp_h": "13.107.18.13",
  "id.resp_p": 443,
  "seen.indicator": "www.slideshare.net",
  "seen.indicator_type": "Intel::DOMAIN",
  "seen.where": "X509::IN_CERT",
  "seen.node": "so16-enp0s8-1",
  "matched": [
    "Intel::DOMAIN"
  ],
  "sources": [
    "from http://hosts-file.net/fsa.txt via intel.criticalstack.com"
  ],
  "fuid": "FnRp0j1YMig5KhcMDg",
  "file_mime_type": "application/x-x509-user-cert",
  "file_desc": "13.107.18.13:443/tcp"
}
{
  "ts": "2019-03-12T18:32:19.821962Z",
  "uid": "CvusFJ2HdbTnCLxEUa",
  "id.orig_h": "192.168.4.6",
  "id.orig_p": 64826,
  "id.resp_h": "13.107.42.14",
  "id.resp_p": 443,
  "seen.indicator": "www.slideshare.net",
  "seen.indicator_type": "Intel::DOMAIN",
  "seen.where": "X509::IN_CERT",
  "seen.node": "so16-enp0s8-1",
  "matched": [
    "Intel::DOMAIN"
  ],
  "sources": [
    "from http://hosts-file.net/fsa.txt via intel.criticalstack.com"
  ],
  "fuid": "FUrrLa45T7a8hjdRy",
  "file_mime_type": "application/x-x509-user-cert",
  "file_desc": "13.107.42.14:443/tcp"
}

```

-------------------------------------------------------------


<h3 align="center">Zeek Intel logical Diagram</h3>

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/f3ad8ff3-0c7a-4418-83c6-16820f2603b2" />
