<h1 align="center"> Titan Network L2 Edge Node Cassini Testnet Ubuntu Kurulum </h1>

* [Titan Website](https://test1.titannet.io/login)<br>
* [Titan Discord](https://discord.com/invite/titannet)<br>
* [Titan Telegram](https://t.me/titannet_dao)<br>

Kurulumdan önce üstteki websiteye girip kaydolduktan sonra "console" > "node management" > "get identity code" kısmında identity code almanız gerekiyor. Birazdan lazım olacak. Ayrıca tüm nodelarımızı "node management" kısmından kontrol edebiliriz.

### Gereklilikleri yükleyelim
```
sudo apt update && sudo apt upgrade -y
sudo apt install screen
```

### İşlemleri screen içinde yapıyoruz
```
screen -S titan
```

### Titan Network dosyasını indirelim
```
wget https://github.com/Titannet-dao/titan-node/releases/download/v0.1.19/titan-l2edge_v0.1.19_patch_linux_amd64.tar.gz
```

### Titan Network dosyasını çıkartalım
```
tar -xzf titan-l2edge_v0.1.19_patch_linux_amd64.tar.gz
```

### Titan Network dosyasına gerekli izinleri verelim ve açalım işlemleri burada yapacağız
```
chmod +x /root/titan-edge_v0.1.19_89e53b6_linux_amd64/titan-edge
cd /root/titan-edge_v0.1.19_89e53b6_linux_amd64/
```


### Gerekli kütüphane değişkenini tanımlayalım ve nodu çalıştıralım
```
İlk kurulumdan sonraki ilk çalıştırma
export LD_LIBRARY_PATH=/root/titan-edge_v0.1.19_89e53b6_linux_amd64:$LD_LIBRARY_PATH

./titan-edge daemon start --init --url https://cassini-locator.titannet.io:5000/rpc/v0
```

### Nodu titan hesabımıza bağlayalım identity-code burada lazım
```
titan-edge bind --hash=your-hash-here https://api-test1.container1.titannet.io/api/v2/device/binding
```

### Nod durursa veya sorun olursa yeniden çalıştırmak için
```
titan-edge daemon start
```

### Nodu durdurmak için
```
titan-edge daemon stop
```

### Kurulumdan sonra ana ekrana dönmek için
```
ctrl+a aynı anda bastıktan sonra screen ekranı komut modu açılır sonrasında +d ye basarak ana ekrana dönebilirsin
```

### Çıktın kapattın sonrasında yeniden açtın ve kontrol etmek istedin
```
screen -r -d titan
```

### Birden fazla screen komutun var adını hatırlayamadın
```
screen -ls (hepsini görüntüler id ile birlikte) 
```

### Açık olan herhangi bir screeni kapatmak istedin
```
screen -X -S screenid quit
```