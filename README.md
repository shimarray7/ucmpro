═══════════════════════════════════════════════════════════════════════
  UCM PRO — Ultimate Club Manager
  README para Claude Code
  Última atualização: Março 2026
═══════════════════════════════════════════════════════════════════════

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  O PROJETO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Gerenciador de clubes de futebol brasileiro, single-file HTML/CSS/JS.
Desenvolvido por Adriano (MEI — design e edição de vídeo), brasileiro.
Site: ucmpro.com.br | Hospedagem: Netlify | Domínio: SuperDomínios

ARQUIVO PRINCIPAL: index.html (~1.302 KB, ~17.811 linhas)
Não há arquivos separados de CSS ou JS — tudo está em um único arquivo.


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ARQUIVOS NA PASTA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

index.html              → Jogo COMPLETO (sem limitador de demo)
index-DEMO.html         → Versão demo (limitada a 5 partidas jogadas)
                          Para gerar nova demo: buscar DEMO_LIMIT no
                          index.html e adicionar linha conforme README_DEMO.txt
README.txt              → Este arquivo (contexto para Claude Code)
README_DEMO.txt         → Instruções para gerar/remover limitador de demo


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ESTRUTURA DO index.html
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

O arquivo tem as seguintes seções em ordem (buscar pelos comentários ═══):

  1. <style>          → CSS completo (tokens, animações, componentes)
  2. DATA — CLUBS     → const CLUBS = [...] — 60 clubes (A/B/C)
  3. DATA — SQUADS    → const REAL_SQUADS = {...} — elencos dos 20 clubs A
  4. DATA — EVENTS    → SEASON_EVENTS, TRASH_TALK, RIVAL_MANAGERS
  5. HELPERS          → funções utilitárias (R, C, FM, AC, clubLogo, etc.)
  6. NAVIGATION       → goTo(), renderHome(), navTo()
  7. MATCH ENGINE     → startMatch(), buildMatchEvents(), simulateHalf()
  8. TRANSFER SYSTEM  → buildMarket(), renderInbox(), showTransferDetail()
  9. SEASON END       → showSeasonEnd(), startNextSeason(), buildSeasonNarrative()
  10. GAME OVER       → gameOverReturnMenu(), showDemoLimit()
  11. SAVE SYSTEM     → save(), loadSlot(), getAllSlots(), renderMenuSlots()
  12. RENDER fns      → renderCalendar(), renderSquad(), renderStadium(), etc.
  13. INIT            → bloco de inicialização ao carregar a página


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DADOS DO JOGO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CLUBES:
  - 20 clubes na Divisão Elite  (div:'A')
  - 20 clubes na Segunda Divisão (div:'B')
  - 20 clubes na Terceira Divisão (div:'C')
  - Total: 60 clubes, todos com nomes e estádios fictícios/genéricos

ELENCOS (REAL_SQUADS):
  - 20 clubes da Divisão Elite têm elencos fixos com 17-22 jogadores cada
  - Os outros 40 clubes (B e C) têm elencos gerados proceduralmente
  - Função buildSquad() gera elencos com nomes únicos por clube
  - Pool de nomes: FN (40 primeiros nomes) × LN (40 sobrenomes) = 1.600 combinações

LOGOS SVG:
  - 20 clubes da Divisão Elite têm logos SVG (base64 webp embedded)
  - Logos da Segunda e Terceira Divisão ainda não foram adicionados (PENDENTE)
  - Função clubLogo(id, size, cls) renderiza o logo ou fallback emoji
  - Logos estão armazenados no objeto SVG_LOGOS dentro do <script>

SISTEMAS IMPLEMENTADOS (40/40):
  ✅ Partidas ao vivo com narração
  ✅ 37 tipos de decisões táticas
  ✅ 38 rodadas por temporada, multi-temporada ilimitada
  ✅ 3 competições paralelas (Copa Nacional, Continental, Copa Sul)
  ✅ Copa Continental: qualificação por posição final (top 4 → Cont., top 6 → Sul)
  ✅ Mercado de transferências + janelas (TW_WINDOWS)
  ✅ Inbox (caixa de mensagens) com tipos: incoming_offer, sell_response,
     outgoing_response, counter_response, trash_talk
  ✅ Moral dos jogadores + personalidades (guerreiro, líder, técnico, etc.)
  ✅ Satisfação da torcida + métricas de fanSatisfaction
  ✅ Sistema de rivais (rivalOffer, trash talk entre técnicos)
  ✅ Estádio upgrades (8 melhorias, receita de bilheteria)
  ✅ Patrocínios com contratos por temporada
  ✅ Comissão técnica (staff: CT, médico, olheiro, preparador)
  ✅ Infraestrutura (base de jovens, analytics, etc.)
  ✅ Objetivos da diretoria (buildBoardObjectives)
  ✅ Sistema de saves: 3 slots no localStorage + exportar/importar JSON
  ✅ Promoção/rebaixamento: top 4 sobe, bottom 4 desce em cada divisão
  ✅ CPU clubs se movem entre divisões ao fim de cada temporada (simulateCpuMovement)
  ✅ Game Over: bottom 4 da Terceira Divisão encerra a carreira
  ✅ Narrativa entre temporadas por divisão e resultado (buildSeasonNarrative)
  ✅ Logos nos slots de save, halftime, result overlay, calendário, inbox
  ✅ Estádios com nomes genéricos para todos os 60 clubes


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  FUNÇÕES CRÍTICAS — SABER ONDE ESTÃO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

clubLogo(id, size, cls)
  → Renderiza logo SVG ou emoji fallback. Retorna HTML string.
  → SEMPRE usar innerHTML para receber o resultado, NUNCA textContent.

showSeasonEnd()
  → Tela de fim de temporada. Chama simulateCpuMovement() e buildSeasonNarrative().
  → Detecta Game Over: curDiv === 'C' && pos >= totalTeams()-3

startNextSeason()
  → Reseta dados da temporada, reconstrói tabela com clubes da nova divisão.
  → Qualificação para Copa Continental: _prevSeasonPos <= 4
  → Qualificação para Copa Sul: _prevSeasonPos entre 5 e 6

simulateCpuMovement(playerPos, playerDiv)
  → Move 4 clubes entre cada fronteira de divisão ao fim da temporada.
  → Chamada dentro de showSeasonEnd() após atualizar G.clubDiv.

buildSeasonNarrative(pos, outcome, curDiv)
  → Gera texto da "Crônica da Temporada" com tom específico por divisão.
  → Outcomes: 'champ', 'promo', 'sulam', 'rel', 'ok', 'gameover'

showEventModal(ev)
  → Usa innerHTML (não textContent) para ev-title e ev-context.
  → titleFn e contextFn podem retornar HTML com clubLogo() — ok.

renderReportDrawer(r)
  → r deve ter: hcId, acId, hcName, acName, hg, ag, result, isHome
  → Usa innerHTML com clubLogo() para rdw-subtitle e rdw-score-teams

save() / loadSlot(slot)
  → save(): localStorage key = 'bfm_slot_1', 'bfm_slot_2', 'bfm_slot_3'
  → loadSlot(): restaura CLUBS[club].div = G.clubDiv após carregar
  → Legacy migration: 'bfm_v4' → 'bfm_slot_1' na primeira inicialização

RN() → FN[random] + ' ' + LN[random]  (nomes aleatórios genéricos)
_uniqueName() → versão com Set para evitar duplicatas (usada em buildSquad)
_mktName()    → versão com Set para mercado (usada em buildMarket)


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DIVISÕES — NOMES E HELPERS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

divName(d)  → {A:'Divisão Elite', B:'Segunda Divisão', C:'Terceira Divisão'}
divShort(d) → {A:'Liga Nacional', B:'Segunda Divisão', C:'Terceira Divisão'}
divComp(d)  → {A:'Brasileiro', B:'Segunda Divisão', C:'Terceira Divisão'}
divNextUp(d)   → {A:null, B:'A', C:'B'}
divNextDown(d) → {A:'B', B:'C', C:null}
totalTeams()   → G.table.length (normalmente 20)

Zonas por temporada (20 times):
  - Top 4  → promoção ou Copa Continental (na Elite)
  - Top 6  → Copa Sul (na Elite apenas)
  - Bottom 4 (pos >= 17) → rebaixamento
  - Bottom 4 na Terceira Divisão → GAME OVER


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  PROTEÇÃO JURÍDICA — ITENS VERIFICADOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Nomes de clubes: todos fictícios (ex: Flamengo → Urubu FC)
✅ Logos/escudos: criações originais (SVG gerado), sem cópia de escudos reais
✅ Jogadores: nomes gerados proceduralmente, sem jogadores reais
✅ Competições: nomes genéricos (Liga Nacional, Copa Continental, Copa Sul)
✅ Estádios: todos com nomes genéricos (ex: Vila Belmiro → Vila dos Santos)
✅ Aviso legal no site: "jogo para entretenimento, conteúdo fictício"
⚠️  Estados brasileiros reais (SP, RJ, RS...) são usados — sem problema jurídico


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  PENDÊNCIAS ABERTAS (próximas melhorias)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ALTA PRIORIDADE:
  [ ] Logos SVG dos 20 clubes da Segunda Divisão (Adriano vai enviar os SVGs)
  [ ] Logos SVG dos 20 clubes da Terceira Divisão (Adriano vai enviar os SVGs)
  [ ] Integração Supabase (auth + saves na nuvem) para versão paga
  [ ] Tela de login in-game para versão paga

MÉDIA PRIORIDADE:
  [ ] Elencos fixos (REAL_SQUADS) para clubes da Segunda Divisão
  [ ] Mais eventos sazonais (atualmente 38, meta: 60+)
  [ ] Narrativa entre temporadas mais variada (mais frases por cenário)

BAIXA PRIORIDADE:
  [ ] Movimento dos adversários CPU com elencos envelhecendo entre temporadas
  [ ] Histórico de temporadas anteriores visível na tela do clube
  [ ] Mais tipos de patrocínios e contratos


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEMO LIMIT — COMO FUNCIONA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

O limitador está em startMatch(), primeira linha do corpo da função:

  /* DEMO_LIMIT — remova esta linha para desbloquear o jogo completo */
  if(G && (G.wins+G.draws+G.losses) >= 5){ showDemoLimit(); return; }

Para REMOVER (versão completa): apagar a linha acima.
Para ADICIONAR (gerar demo): inserir a linha acima como 1ª linha de startMatch().
A função showDemoLimit() já existe no código — não precisa recriar.


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEPLOY — COMO SUBIR ATUALIZAÇÕES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Site de vendas: ucmpro.com.br → Netlify (brilliant-genie-755c5d.netlify.app)
DNS: SuperDomínios
  @ → A → 75.2.60.5
  www → A → 75.2.60.5

Para subir nova versão do SITE:
  1. Arraste o index.html do site para o Netlify (deploy manual)

Para subir nova versão do JOGO (quando tiver Supabase integrado):
  1. O jogo roda em domínio separado: app.ucmpro.com.br
  2. Seguir guia no PDF: UCM_Monetizacao.pdf


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  CONTATO E CONTEXTO DO PROPRIETÁRIO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Nome: Adriano
Perfil: brasileiro, designer e editor de vídeo (MEI)
Nível técnico: não é programador — prefere instruções claras e diretas
Ferramentas: trabalha com Photoshop, Trello, WordPress, Netlify
Estilo de trabalho: iterativo, prefere outputs de produção prontos para uso


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DICAS PARA O CLAUDE CODE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. O arquivo é grande (~17.800 linhas). Use busca por termos específicos
   em vez de ler o arquivo inteiro. Exemplos de âncoras úteis:
   - "DATA — CLUBS"     → início do array CLUBS
   - "DATA — SQUADS"    → início do REAL_SQUADS
   - "function startMatch"    → início da partida
   - "function showSeasonEnd" → fim de temporada
   - "function renderCalendar" → calendário
   - "function renderInbox"   → caixa de mensagens
   - "DEMO_LIMIT"             → limitador da demo

2. Ao editar qualquer elemento visual que recebe clubLogo():
   - Verificar se usa innerHTML (correto) ou textContent (errado)
   - clubLogo() retorna HTML string — nunca pode ir para textContent

3. Ao adicionar logos de novos clubes (Segunda e Terceira Divisão):
   - Formato SVG: <?xml...><svg xmlns... viewBox="0 0 500 500">
     <image x="0" y="0" width="500" height="500" xlink:href="data:image/webp;base64,..."/>
   - Adicionar no objeto SVG_LOGOS com a chave = club id
   - Testar com clubLogo('id_do_clube', 36)

4. Para testar mudanças: abrir index.html direto no navegador Chrome/Firefox
   Não precisa de servidor local — o jogo funciona como arquivo local.

5. Ao fazer edições, prefira str_replace cirúrgico em vez de reescrever
   seções inteiras — menor risco de apagar código funcional.

═══════════════════════════════════════════════════════════════════════
