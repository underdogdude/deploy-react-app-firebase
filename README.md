# เนื้อหานี้เอามาจาก https://medium.com/muze-innovation/%E0%B8%A1%E0%B8%B2%E0%B8%A5%E0%B8%AD%E0%B8%87-deploy-create-react-app-%E0%B8%82%E0%B8%B6%E0%B9%89%E0%B8%99-firebase-hosting-%E0%B9%81%E0%B8%A5%E0%B8%B0%E0%B8%97%E0%B8%B3-ci-cd-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-travis-ci-%E0%B8%81%E0%B8%B1%E0%B8%99%E0%B9%80%E0%B8%96%E0%B8%AD%E0%B8%B0-7a010a2005ed

ให้เครดิตเค้าด้วย
เอามาใส่ใน github นี้เอาไว้กันลืมเฉยๆ




# ติดตั้ง create-react-app เพื่อสร้างโปรเจคที่พร้อมให้เรา dev ด้วย React.js

[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*YCAkjW_7y5n_Ns6Akchkjg.png)](https://cdn-images-1.medium.com/max/1000/1*YCAkjW_7y5n_Ns6Akchkjg.png)

# ติดตั้ง create-react-app เพื่อสร้างโปรเจคที่พร้อมให้เรา dev ด้วย React.js

  - ติดตั้ง create-react-app cli
    ``` npm install -g create-react-app ```
  - หลังจากติดตั้งเสร็จแล้วให้ทำการสร้างโปรเจคด้วยคำสั่ง
    ```  create-react-app <ชื่อแอพ> ```

ตัวอย่างเช่น ผมจะตั้งชื่อโปรเจคว่า deploy-react-firebase-example ให้รันคำสั่ง 
   ``` create-react-app deploy-react-firebase-example ```
   
- ลองรันโปรเจคดูว่าใช้งานได้มั้ย โดยให้เข้าไปในโปรเจคที่พึ่งสร้างขึ้น หลังจากนั้นทำการรันด้วยคำสั่ง  ``` npm start ```เพื่อทำการ start server

- ลองทดสอบดูว่าเว็ปเราสามารถรันได้รึเปล่า ทำการเปิด browser เข้าไปที่ url “http://localhost:3000” ถ้าเห็นหน้าตาเว็ปประมาณนี้แสดงว่า ผ่าน!
______________________
# มา deploy web ของเราขึ้น Firebase hosting กัน

- เข้าไปที่ https://console.firebase.google.com/ ทำการสมัครให้เรียบร้อย
- เมื่อเข้าไปยัง Firebase dashboard ให้ทำการสร้างโปรเจคใหม่ โดยกดท่ี Add project -> ทำการตั้งชื่อโปรเจค โดยผมจะใช้ชื่อโปรเจคว่า “deploy-react-firebase-example”

[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*MSdVXsSUJ7QkwP43yjZvxQ.png)](https://cdn-images-1.medium.com/max/1000/1*MSdVXsSUJ7QkwP43yjZvxQ.png)

- เปิด terminal/cmd พิมพ์คำสั่ง``` npm install -g firebase-tools``` เพื่อทำการลง firebase cli หลังจากลงเสร็จเรียบร้อยแล้ว ให้พิมพ์คำสั่ง``` firebase login``` เพื่อ login เข้าสู่ระบบ firebase
- คราวนี้กลับมาที่ project React ของเรา หลังจากนั้นพิมพ์คำสั่งfirebase init เพื่อทำการสร้างค่า config เริ่มต้นของ firebase โดยในขั้นตอน “Select a default Firebase project for this directory” ให้เลือกโปรเจคที่เราสร้างใว้ใน ตอนแรก เช่นของผมคือ “deploy-react-firebase-example” เมื่อเสร็จแล้วเราจะได้ไฟล์มาสองไฟล์คือ firebase.json และ .firebaserc

[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*JUJm7G5cwz_MY2ycSEgokQ.png)](https://cdn-images-1.medium.com/max/1000/1*JUJm7G5cwz_MY2ycSEgokQ.png)


[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*NfOxqaHyIvYLLacTNnHpuw.png)](https://cdn-images-1.medium.com/max/1000/1*NfOxqaHyIvYLLacTNnHpuw.png)

- ให้ทำการ config ที่ไฟล์ firebase.json เพื่อกำหนด public path ดัง

```sh 
{
  "hosting": {
    "public": "build"
  }
}
```
- สังเกตว่าตอนนี้โปรเจคเรายังไม่มี folder build เนื่องจากเรายังไม่ได้ build source code ให้เราทำการพิมพ์คำสั่ง npm run build เพื่อทำการ build source code ของเรา ซึ่งเราจะได้ code ที่ถูก build จะอยู่ใน folder build
- 
[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*hRQqcIzEHealK5-jEe_ofw.png)](https://cdn-images-1.medium.com/max/1000/1*hRQqcIzEHealK5-jEe_ofw.png)

- ขั้นตอนนี้เป็นขั้นตอนสำคัญ เรากำลังจะ deploy web ของเราขึ้น firebase hosting แล้วนะ เย้! ให้เราพิมพ์คำสั่ง``` firebase deploy``` รอจนคำสั่งทำงานจบถ้า deploy สำเร็จมันจะขึ้นว่า “Deploy complete!” เพียงเท่านี้เราก็จะได้เว็ปไซต์ที่สามารถนำไปอวดชาวบ้านได้แล้วครับ XD

- ทดสอบว่าเว็ปที่เราพึ่ง deploy ขึ้นไปใช้งานได้รึเปล่า โดนให้เข้าผ่าน url ที่ใน console บอกตอนที่เรา deploy สำเร็จ สำหรับของผมคือ https://deploy-react-firebase-example.firebaseapp.com (เห้ยย ขึ้นด้วยย)
- นอกจากนี้เราสามารถเข้าไปดูสถานะการ deploy การ roll back และ ทำการเชื่อมต่อกับ domain name ของเรา ผ่าน firebase console(บทความหน้าจะมาสอนเรื่องการเชื่อมต่อกับ domain name นะครับ)

__________________________________________
# มาทำ CI/CD ด้วย Travis-ci กันเถอะ
[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*0en_sPbBm8UCbo66qKMnJg.png)](https://cdn-images-1.medium.com/max/1000/1*0en_sPbBm8UCbo66qKMnJg.png)

จากขั้นตอนที่ผ่านมาจะสังเกตได้ว่า ถ้าเราต้องการ deploy app ของเรา เราก็ต้องรันคำสั่ง``` firebase deploy``` ใช่มั้ยครับ ซึ่งทุกครั้งๆที่เรามีการแก้โค้ดแล้วอยาก deploy เราก็ต้องรันคำสั่ง``` firebase deploy ```ตลอด เป็นไปได้มั้ยที่เราแค่ push code ของเราไปที่ branch ซักที่นึง(เช่น master) แล้วให้มันทำการ build และ deploy ให้เราอัตโนมัติ คำตอบคือ “เป็นไปได้ครับ!” โดยเราจะใช้ travis-ci นี่แหละเป็นตัวช่วยเรา
โดย flow การทำงานจะประมาณนี้ครับ

[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*1DxmMKwlf2WV8bM5hwwAqw.png)](https://cdn-images-1.medium.com/max/1000/1*1DxmMKwlf2WV8bM5hwwAqw.png)


มาเริ่มกันเลยดีกว่า!
 - เข้าไปที่ https://travis-ci.org/ ให้ทำการ sign in ด้วย github account
 - หลังจาก sign in สำเร็จจะเห็นหน้า dashboard ที่แสดงโปรเจคทั้งหมดใน github ของเรา ซึ่งในตัวอย่างผมได้ทำการสร้างโปรเจคใน github ชื่อ deploy-react-firebase-example

[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*zhAj-0E09NqB2zSz1kOuOA.png)](https://cdn-images-1.medium.com/max/1000/1*zhAj-0E09NqB2zSz1kOuOA.png)

* ให้ทำการคลิก check box ให้เป็นเครื่องหมายถูกสีเขียว
* กดคลิกเข้าไปที่ชื่อโปรเจค หลังจากกดเข้าไปจะเจอหน้านี้ครับ

[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*wfjyJ05IaUBX55PI24Gdow.png)](https://cdn-images-1.medium.com/max/1000/1*wfjyJ05IaUBX55PI24Gdow.png)

ให้เราทำการกลับไปที่โปรเจคและทำการสร้างไฟล์ .travis.yml ย้ำ! อย่าลืม . หน้า travis นะครับ ย้ำอีกครั้ง “.travis.yml” นะครับ โดยในไฟล์ .travis.yml ให้ทำการเขียน script ดังนี้ ทำการ commit และ push code ไปที่ master

```sh
cache:
  directories:
  - node_modules # cache node_module
language: node_js # set language to node_js
node_js:
  7 # use node version 7
branches:
  only: 
  - master # auto build and deploy in only master branch
script: # run after installed
- npm install # install node module
- npm run build # build project
install:
  npm install -g firebase-tools # install firebase-cli
after_success:
- firebase use --token ${FIREBASE_TOKEN} # set firebase token
- firebase use --add ${PROJECT_ID} # set current project
- firebase deploy --non-interactive --token "${FIREBASE_TOKEN}" # deploy project
```
- ทำการ generate firebase token เพื่อนำไปใส่เป็นค่า environment variable ใน travis-ci โดยพิพม์คำสั่ง firebase login:ci เราจะได้ firebase token ออกมา

- กลับมาที่หน้าเว็ป travis-ci นำค่า token ที่ได้ไปใส่ใน environment variable โดยให้กดไปที่ tab settings ไปที่ Environment Variables ให้ทำการใส่ค่าดังนี้

> FIREBASE_TOKEN: ค่าที่ได้หลังจากการใช้คำสั่ง login:ci
PROJECT_ID: ดูได้จาก firebase dashboard


[![N|Solid](https://cdn-images-1.medium.com/max/1000/1*j4iT2p4Malxheh4GiqXjjw.png)](https://cdn-images-1.medium.com/max/1000/1*j4iT2p4Malxheh4GiqXjjw.png)


- การ config ทั้งหมดก็มีเท่านี้ครับ คราวนี้เรามาลองเทส ci ของเรากันว่าใช้งานได้รึเปล่า ผมจะเข้าไปแก้รูป logo react หมุนๆให้เป็นหน้าผมหมุนๆแทน 555 แล้วลอง push ขึ้น branch master นะครับ


# จบแล้ว
