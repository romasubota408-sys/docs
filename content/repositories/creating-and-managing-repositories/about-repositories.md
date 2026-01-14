<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>ЛР №3 — Верстка CSS / Float / Flexbox (Варіант 4)</title>

  <style>
    /* ====== БАЗОВЕ ОФОРМЛЕННЯ ====== */
    body{margin:0;font-family:Arial, sans-serif;background:#f3f4f6;color:#111;line-height:1.5}
    .wrap{max-width:1100px;margin:0 auto;padding:16px}
    header{background:#111827;color:#fff;border-radius:12px;padding:14px 14px 10px}
    header h1{margin:0 0 6px;font-size:20px}
    header p{margin:0;color:#cbd5e1;font-size:14px}
    nav{margin-top:10px;display:flex;flex-wrap:wrap;gap:8px}
    nav a{
      display:inline-block;padding:8px 10px;border-radius:10px;
      text-decoration:none;background:#1f2937;color:#e5e7eb;border:1px solid rgba(255,255,255,.12);
      font-size:13px
    }
    nav a:hover{background:#0b1220}
    .card{background:#fff;border:1px solid #d1d5db;border-radius:12px;padding:14px;margin-top:14px}
    .muted{color:#4b5563}
    .hint{background:#eef2ff;border-left:5px solid #6366f1;padding:10px;border-radius:10px}
    .hr{height:1px;background:#e5e7eb;margin:14px 0}
    .center{display:flex;align-items:center;justify-content:center}
    .tag{display:inline-block;padding:3px 8px;border-radius:999px;background:#e5e7eb;font-size:12px;margin-left:6px}

    /* ====== “ПЕРЕМИКАЧ РОЗДІЛІВ” БЕЗ JS ====== */
    .page{display:none}
    .page:target{display:block}
    #home{display:block}
    :target ~ #home{display:none}

    /* ====== ЗАВДАННЯ №1 (макет сайту) ====== */
    .siteHeader{background:#0f172a;color:#fff;border-radius:12px;padding:12px}
    .siteHeader .links a{color:#93c5fd;text-decoration:none;margin-right:10px;font-size:14px}
    .siteLayout{display:flex;gap:12px;margin-top:12px}
    .siteAside{width:240px;background:#f9fafb;border:1px solid #e5e7eb;border-radius:12px;padding:12px}
    .siteMain{flex:1;background:#f9fafb;border:1px solid #e5e7eb;border-radius:12px;padding:12px}
    .siteFooter{margin-top:12px;background:#0f172a;color:#fff;border-radius:12px;padding:12px}
    @media(max-width:850px){
      .siteLayout{flex-direction:column}
      .siteAside{width:auto}
    }

    /* ====== ЗАВДАННЯ №2: ТАБЛИЦІ ====== */
    .demoBox{border:1px solid #9ca3af;background:#fff;border-radius:10px;padding:10px}
    .tableFrameFixed{width:900px;max-width:100%;margin:0 auto;border:2px solid #111}
    .tableFrameFluid{width:95%;max-width:1100px;margin:0 auto;border:2px solid #111}
    .t{width:100%;border-collapse:collapse}
    .t td, .t th{border:2px solid #111;padding:10px;vertical-align:top}
    .tHead,.tFoot{background:#fde047;font-weight:bold;text-align:center}
    .tLeft,.tRight{background:#2563eb;color:#111;font-weight:bold;width:20%;text-align:center}
    .tMid{background:#fff;min-height:220px}
    .tRow{height:260px}

    /* ====== ЗАВДАННЯ №2: FLOAT (плаваючі блоки) ====== */
    .floatFrameFixed{width:900px;max-width:100%;margin:0 auto;border:2px solid #111;background:#fff}
    .floatFrameFluid{width:95%;max-width:1100px;margin:0 auto;border:2px solid #111;background:#fff}
    .fHeader,.fFooter{background:#fde047;font-weight:bold;text-align:center;padding:12px;border-bottom:2px solid #111}
    .fFooter{border-top:2px solid #111;border-bottom:none}
    .fLeft{float:left;background:#2563eb;color:#111;font-weight:bold;min-height:260px;padding:10px;border-right:2px solid #111}
    .fRight{float:right;background:#2563eb;color:#111;font-weight:bold;min-height:260px;padding:10px;border-left:2px solid #111}
    .fContent{min-height:260px;padding:10px}
    .clearfix{clear:both}

    .fixed180{width:180px}
    .fixedContent{margin:0 190px}

    .fluid20{width:20%}
    .fluidContent{margin:0 21%}

    /* ====== ЗАВДАННЯ №3: FLEXBOX ВАРІАНТ 4 ====== */
    .flexTitle{font-weight:bold;margin-bottom:8px}
    .frame{
      width:420px;
      border:3px solid #111;
      background:#fff;
      padding:8px;
    }
    .top{
      background:#fde047;
      border:2px solid #111;
      height:55px;
      display:flex;
      align-items:center;
      justify-content:center;
      position:relative;
      font-weight:bold;
    }
    .mini{
      position:absolute;
      left:12px;
      width:110px;
      height:26px;
      background:#fff;
      border:2px solid #111;
    }
    .middle{
      display:flex;
      gap:10px;
      padding:10px 0;
      min-height:240px;
      align-items:stretch;
    }
    .left, .right{
      background:#2563eb;
      border:2px solid #111;
      flex:0 0 30%;
      display:flex;
      align-items:center;
      justify-content:center;
      font-weight:bold;
      color:#111;
    }
    .centerBlock{
      background:#fff;
      border:2px solid #999;
      flex:1;
      display:flex;
      flex-direction:column;
      justify-content:flex-end;
      align-items:center;
      padding:10px;
      position:relative;
      font-weight:bold;
      color:#111;
    }
    .centerBlock .num{
      position:absolute;
      top:10px;
      font-weight:bold;
      color:#111;
    }
    .red{
      width:80%;
      height:38px;
      background:#ef4444;
      border:2px solid #111;
      margin-top:10px;
    }
    .bottom{
      background:#fde047;
      border:2px solid #111;
      height:55px;
      display:flex;
      align-items:center;
      justify-content:center;
      font-weight:bold;
    }

    /* ====== Код (для звіту) ====== */
    pre{background:#0b1020;color:#e5e7eb;padding:12px;border-radius:10px;overflow:auto}
    code{font-family:Consolas, monospace;font-size:12px}
  </style>
</head>

<body>
  <div class="wrap">
    <header>
      <h1>ЛАБОРАТОРНА РОБОТА №3 — Верстка HTML (CSS / Float / Flexbox) <span class="tag">Варіант 4</span></h1>
      <p>Навігація по виконаних завданнях лабораторної роботи.</p>
      <nav>
        <a href="#home">Завдання 1</a>
        <a href="#task2">Завдання 2</a>
        <a href="#flex">Завдання 3</a>
        <a href="#report">Звіт</a>
      </nav>
    </header>

    <!-- ============ ЗАВДАННЯ №1 ============ -->
    <section id="home" class="page">
      <div class="card">
        <h2 style="margin:0 0 6px">Завдання №1: Макет власного сайту</h2>
        <p class="muted" style="margin:0 0 10px">
          Тип макету: <b>класичний багатоколонковий</b> (Header + 2 колонки + Footer), адаптивний.
        </p>

        <div class="siteHeader">
          <b>Мій сайт (демо)</b>
          <div class="links" style="margin-top:6px">
            <a href="#task2">Завдання 2</a>
            <a href="#flex">Завдання 3</a>
            <a href="#report">Звіт</a>
          </div>
        </div>

        <div class="siteLayout">
          <aside class="siteAside">
            <b>Меню</b>
            <ul>
              <li>Новини</li>
              <li>Про мене</li>
              <li>Контакти</li>
            </ul>

            <div class="hint">
              <b>Базова концепція:</b> блокова модель + Flexbox для побудови колонок.
            </div>
          </aside>

          <main class="siteMain">
            <h3 style="margin-top:0">Вміст</h3>
            <p>Макет містить шапку, дві колонки (бічна панель і основний контент) та підвал. Верстка адаптується під ширину екрана.</p>
          </main>
        </div>

        <div class="siteFooter">© ЛР №3. Верстка HTML-документу</div>
      </div>
    </section>

    <!-- ============ ЗАВДАННЯ №2 ============ -->
    <section id="task2" class="page">
      <div class="card">
        <h2 style="margin:0 0 6px">Завдання №2: Таблична верстка + Float-верстка</h2>
        <p class="muted" style="margin:0">
          Реалізовано: фіксована/гумова таблична верстка та фіксована/гумова верстка на плаваючих блоках (float).
        </p>
      </div>

      <div class="card">
        <h3 style="margin:0 0 10px">2.1 Фіксована таблична верстка</h3>
        <div class="demoBox">
          <div class="tableFrameFixed">
            <table class="t">
              <tr><td class="tHead" colspan="3">HEADER (таблиця фіксована)</td></tr>
              <tr class="tRow">
                <td class="tLeft">Ліва<br>колонка</td>
                <td class="tMid">Контент</td>
                <td class="tRight">Права<br>колонка</td>
              </tr>
              <tr><td class="tFoot" colspan="3">FOOTER</td></tr>
            </table>
          </div>
        </div>
      </div>

      <div class="card">
        <h3 style="margin:0 0 10px">2.2 Гумова таблична верстка</h3>
        <div class="demoBox">
          <div class="tableFrameFluid">
            <table class="t">
              <tr><td class="tHead" colspan="3">HEADER (таблиця гумова)</td></tr>
              <tr class="tRow">
                <td class="tLeft">Ліва 20%</td>
                <td class="tMid">Контент (адаптивний)</td>
                <td class="tRight">Права 20%</td>
              </tr>
              <tr><td class="tFoot" colspan="3">FOOTER</td></tr>
            </table>
          </div>
        </div>
      </div>

      <div class="card">
        <h3 style="margin:0 0 10px">2.3 Фіксована float-верстка</h3>
        <div class="demoBox">
          <div class="floatFrameFixed">
            <div class="fHeader">HEADER (float фіксована)</div>

            <div class="fLeft fixed180 center">Ліва</div>
            <div class="fRight fixed180 center">Права</div>
            <div class="fContent fixedContent">Контент (між блоками через margin)</div>

            <div class="clearfix"></div>
            <div class="fFooter">FOOTER</div>
          </div>
        </div>
      </div>

      <div class="card">
        <h3 style="margin:0 0 10px">2.4 Гумова float-верстка</h3>
        <div class="demoBox">
          <div class="floatFrameFluid">
            <div class="fHeader">HEADER (float гумова)</div>

            <div class="fLeft fluid20 center">Ліва 20%</div>
            <div class="fRight fluid20 center">Права 20%</div>
            <div class="fContent fluidContent">Контент (адаптивний)</div>

            <div class="clearfix"></div>
            <div class="fFooter">FOOTER</div>
          </div>
        </div>
      </div>
    </section>

    <!-- ============ ЗАВДАННЯ №3 FLEXBOX ============ -->
    <section id="flex" class="page">
      <div class="card">
        <h2 style="margin:0 0 6px">Завдання №3: FLEXBOX — Варіант 4</h2>
        <p class="muted" style="margin:0 0 10px">
          Розміщення блоків відповідає схемі: 1 (верх), 2 (ліва колонка), 3 (центр + червоний блок знизу), 4 (права колонка), 5 (низ).
        </p>

        <div class="flexTitle">Варіант 4 (Flexbox)</div>
        <div class="frame">
          <div class="top">
            <div class="mini"></div>
            1
          </div>

          <div class="middle">
            <div class="left">2</div>

            <div class="centerBlock">
              <div class="num">3</div>
              <div class="red"></div>
            </div>

            <div class="right">4</div>
          </div>

          <div class="bottom">5</div>
        </div>
      </div>
    </section>

    <!-- ============ ЗВІТ ============ -->
    <section id="report" class="page">
      <div class="card">
        <h2 style="margin:0 0 6px">Звіт до лабораторної роботи №3</h2>

        <h3>Тема</h3>
        <p>ВЕРСТКА HTML-ДОКУМЕНТУ. ВЕРСТКА ЗАСОБАМИ CSS та FLEXBOX.</p>

        <h3>Мета</h3>
        <ul>
          <li>Придбати практичні навички верстки сторінок засобами CSS та плаваючих елементів (float), визначити їх переваги й недоліки.</li>
          <li>Придбати практичні навички верстки сторінок засобами CSS та FLEXBOX.</li>
        </ul>

        <h3>1) Місце розташування сайту та звітного документу</h3>
        <p>Файл виконання лабораторної роботи збережено у вигляді HTML-документа <b>lr3.html</b>.</p>

        <h3>2) Завдання №1 — макет власного сайту</h3>
        <p><b>Тип макету:</b> класичний багатоколонковий (Header + 2 колонки + Footer), адаптивний.</p>

        <h3>3) Базова концепція верстки засобами CSS</h3>
        <p>Під час верстки застосовано блокову модель (Box Model), роботу з відступами (margin/padding) та Flexbox для розміщення колонок і вирівнювання елементів.</p>

        <h3>4) Скріншот головної сторінки</h3>
        <p class="hint"><b>Рисунок 1 – Головна сторінка сайту.</b> (вставити скрін з розділу “Завдання 1”)</p>

        <h3>5) HTML-програмний код макету власного сайту</h3>
        <p class="muted">Код макету знаходиться у цьому файлі в розділі “Завдання 1” (HTML-структура) та у секції &lt;style&gt; (CSS-оформлення).</p>

        <h3>6) Завдання №2 — сторінки верстки (таблиця / float)</h3>
        <p>У роботі реалізовано табличну верстку (фіксовану та гумову) і блокову верстку на плаваючих елементах (фіксовану та гумову).</p>

        <h3>7) Висновки: таблиці vs блоки (float)</h3>
        <p><b>Таблична верстка:</b> проста для табличних даних, але не підходить як сучасний спосіб побудови макетів (складніше підтримувати й адаптувати).</p>
        <p><b>Float-верстка:</b> дозволяє створювати колонки, але потребує очищення потоку (clearfix), у великих макетах менш зручна ніж Flex/Grid.</p>

        <h3>8–9) Завдання №3 — FLEXBOX (варіант 4)</h3>
        <p>Сторінка виконана технологією Flexbox. Середня частина побудована як flex-контейнер з трьома блоками (2, 3, 4), центральний блок займає решту ширини (flex:1), а червоний блок у ньому розміщено внизу завдяки flex-direction:column.</p>
        <p class="hint"><b>Рисунок 2 – Сторінка, виконана технологією Flexbox (варіант 4).</b> (вставити скрін з розділу “Завдання 3”)</p>

        <h3>10) Загальні висновки</h3>
        <p>У лабораторній роботі виконано макет сайту та реалізовано різні способи верстки: табличний, блоковий на float та Flexbox. Flexbox є найбільш зручним для сучасної верстки, оскільки спрощує розміщення елементів, вирівнювання та побудову колонок, а також краще підходить для адаптивних макетів.</p>
      </div>
    </section>

  </div>
</body>
</html>
